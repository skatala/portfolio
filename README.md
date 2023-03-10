# Portfolio
I'm Sam, an aspiring programmer from Germany.  
This site is just to show some of my university and hobby projects.

### About Me

In my free time I like to program games, play electric guitar, play games of all kinds with friends i.e. video, board, and pen and paper games.
Other hobbies of mine include getting around on 2 wheels, mostly bicycling and motorbike riding.
When I'm alone and just want to relax I love to read books like The Way of Kings.
I love listening to music, while programming or reading or just because. My favorite artists include Lana Del Rey, Kyuss and the Black Keys.

### Skills
- Java, this is the language I have used the most outside of Game Development, I have created for my Bachelor Thesis a multithreaded and fully networked system using Java's Secure Sockets for BLS Elliptic Curve Threshold Signatures, wrapping the MIRACL crypto library and using their elliptic curve implementation to implement all protocol logic. The resulting system is very versatile in that it supports the most prominent elliptic curves of 100-256bits security level.
- C++, during my research assistant work I have worked with heavily templated codebases. I feel comfortable enough in C++ and the STL to do most tasks in it, but am by no means an expert
- JS, for my most recent browser based project CurveMp, I used peerjs and JS logic for getting data from the Game to other players.
- Networking, the distributed system created for my Bachelor's thesis was fully connected and tested to run on two different directly connected hosts that were part of the university chair's testbed that had the virtualization capability for hundreds of nodes. For the nodes I have implemented a minimalistic application layer protocol that sits on top of TLS that has much less overhead than using preexisting protocol solutions like protobuf. The entire system was managed using the testbed's orchestrating system.
- Multithreading, I have good knowledge of Multithreading principles having worked with threadpools and async programming primitives like Golang's go routines or Unity's coroutines.
- Unity 3D and C#, as this is the game framework that I have used the most I feel very comfortable with it
- HLSL, I have written many shaders in HLSL for DirectX and Unity projects, some can be seen in action in the game Kingdom Dawn under my University Projects.
- DirectX, I have created a bare-bones 3D Game using C++, DirectX and HLSL. Sometime I would like to try myself at creating a VR game using the OpenVR API, C++ and DirectX or another Graphics API.

## Hobby Projects

### CurveMP, Achtung die Kurve

Browser based multiplayer game inspired by Achtung die Kurve. Made in Unity3D using C# and peerjs for networking.

<img src="https://raw.githubusercontent.com/skatala/portfolio/main/img/curve.png" alt="curve.PNG" />

<details>
  <summary>How to play</summary>
  <p>
  The game is accessible here https://rigotheshtanid.itch.io/curvemp with the password 3989c91e73b67593faf8136237bd92c3.
  Currently supports 2-4 players. 
  </p>
</details>

<details>
  <summary>Some Technical Details</summary>
  <p>
  This is a game that I made for friends and myself, inspired by games like CurveFever and Achtung, die Kurve. I wanted a game where friends can just jump in without signing up or clicking through a three different menu screens before getting paralyzed by a ton of different game modes.
  </p>
  <p>
  It uses peerjs to enable peer-to-peer multiplayer in the browser and the game itself is made in Unity3D  and C#. The interop between JS and C# is made possible by Unity3D as it uses emscripten to compile to the "WebGl" platform. Emscripten provides the functionality of memory shared arrays which get used to transfer most of the packets from C# to the JS based peerjs networking functions.

  </p>
  <p>
  Classically a game you play local-multiplayer in the Browser, there now exist browser based multiplayer versions, the networking for these is not to my liking for playing with friends, as they are geared towards the largest audience possible including optimizing the games so they can be played with the worst possible internet connection. Technologies used in general for this purpose are things like Client and Serverside prediciton, input buffering and more. These techniques can lead to inconsistencies between client and server state e.g. causes the classic getting shot behind walls problem and the phenomenon where lag-switches can be used to exploit the favourable server-side treatment of lagging clients. These inconsistencies can be felt in CurveFever. These in addition to all the features that were just tacked on for monetization made me want to make an alternative that me and my friends could enjoy more.
  </p>
</details>



 

### Password Generator


<img src="https://raw.githubusercontent.com/skatala/portfolio/main/img/passwordgen.png" alt="passwordgen.PNG" />


I wrote a small tool for generating secure and memorable passphrases by sampling words at random from language word lists. The program gives an estimation of security of the chosen parameters as well as double checks whether all individual words do not fall into a top 10k most frequent words subset.  

Accesible here:  https://github.com/skatala/passwordgen
Download .exe: https://github.com/skatala/passwordgen/releases/tag/v0.9.0

## University Projects

### Kingdom Dawn

Watch the trailer here:  
[![Trailer](http://img.youtube.com/vi/VrJTRM2MyzY/0.jpg)](http://www.youtube.com/watch?v=VrJTRM2MyzY "KingdomDawn Trailer")  

This game was conceived with my idea of trying to make a game that looks like the strategic map from Age of Wonders 3.  
I implemented the world generator and the entire game board drawing and interaction system based internally on a hex grid.  
For the treasure map look I wrote some basic shaders e.g. world space aligned textures for the river/water, that overlays the correctly aligned waves over all hexes independent of the individual hex's rotation. I think we came very close to the original vision.

For anyone interested in some technical details:
<details>
  <summary>Show</summary>
  <p>
  One simple but effective optimization I like is that instead of using Unity's Raycast system to determine which hex the user mouses over we use a hex grid to world matrix and it's inverse to do that math.  
  Internally the hexes are structured as a 2D array so this way all it takes is transforming the mouse coords to hex grid coords with some matrix multiplication and we're done.
  </p>
  <p>
  One initially tricky aspect that had a simple (kind of) solution was creating a system for determining whether the river hexes had to be rotated and to which orientation. This is so our artist doesn't have to rotate all the hexes manually. 
  </p>
  <p>
  We used bitmasks to encode which of the hex neighbors had water on it to determine which exact kind of river/ocean tile has to be instantiated at these positions. By concatenating the bitmask to itself we can then bitshift a target bitmask over it, to determine the degree of rotation. E.g. 0b111000 encodes a hex tile whose first 3 neighbors clockwise contain water. Now if we shift this bitmask with wraparound (rotate) we can match all rotations of hex tiles with 3 consecutive water neighbors. Now our artist only had to create assets for all 14 base bitmasks and created some variations of the most used assets to introduce more variety to the look of rivers and oceans (0b1, 0b11, 0b111..., 0b1011, 0b1101...) and not the entire set that can be acquired through rotation.
  </p>
</details>

<details>
  <summary>Unpopulated World Screenshots</summary>
  <img src="https://raw.githubusercontent.com/skatala/portfolio/main/img/world2.png" alt="world2.PNG" />
  <img src="https://raw.githubusercontent.com/skatala/portfolio/main/img/world1.png" alt="world1.PNG" />
</details>



### My First game: Dig Simulator

<details>
  <summary>Screenshot</summary>
 <img src="https://raw.githubusercontent.com/skatala/portfolio/main/img/digsim.png" alt="digsim.PNG" />
</details>

When I was 16 I programmed this masterpiece in JavaScript with the HTML canvas as the "engine". The game has a basic particle system and procedurally generated levels with ore veins. With each stage new ores get phased in and old ones get phased out. A friend of mine did the UI/CSS parts of it. You play as a blue square trying to mine as much downward as possible, craft bombs and use them. Upgrade your vision radius, bombs and drill. Every level has an Enemy in it, if it smells more cash on you than it has, it will come for you immediately, otherwise it will mind it's own business until you come close enough.  
You can play it [here, (hosted on my friend's site)](https://codepen.io/TurtleTurret/full/OXoGxj). 

For some technical details, will bore many but might amuse some:
<details>
  <summary>Make me cry</summary>
  <p>
Because at this point I had only programmed in Java before, I was immediately missing the concept of classes, so instead of using typescript for whatever reason we found this online tool that generated the JavaScript prototype code from typescript for you or something of the sort, which results code that is barely readable at best. ???
 </p>
 <p>
Some technical issues I faced during development include: terrible performance. The game was playable with 15fps max and I couldn't understand how the performance could be so bad (even for Javascript back then). Turns out that I was overdrawing every frame twice: Of course, the game board has to be reset (it doesn't) so I thought better update the 2D array which indexes the game blocks to a neutral color every frame. This works because the generated levels are stored in a separate 3D array, so we can just copy the relevant 2D array out of the 3D array into the buffer array. Every Frame. Twice. If you're thinking WHY? I agree. Well, this was fixed, in the end only what changes from frame to frame get's drawn on the screen as is reasonable to do. For the explosion effects I thought it would be neat to have the letters of the word "boom" serve as the particles for the explosion, the end result is kind of cool.
  For this I ended up implementing some sort of list of particles that had a time to live and direction that was iterated every frame. I then ended up using the same system for animating the digging, which is just a bunch of pixels spraying from the center of a block into random directions. If you made it this far, thank you for reading!
 </p>
</details>



## More University Projects

The next university projects aren't really games for the sake of being games but more like games for the sake of using specific technology.

#### 3D Pose Estimation
One Project was about using 3D Pose estimation which resulted in this game:
<details>
  <summary>Screenshot</summary>
 <img src="https://raw.githubusercontent.com/skatala/portfolio/main/img/poseestimation.png" alt="poseestimation.PNG" />
</details>
  
The gameplay consists of memorizing movements of how to move your arms to activate spells to defeat the enemies before they defeat you.  
It's a bit janky, because it works with all cameras, and most cameras not purpose built for real time computer vision suffer from horrible latency issues. In this game it's not that bad because the player is not reacting to anything but planning the next spell. The other issue is the frame-rate of the estimation. The pose estimation neural net that we were provided is quite heavy and on a bad day you can easily miss out on a 10th of a second, which is enough to miss out on a gesture if you're moving as quick as possible. In summary, had we had been provided special cameras it would've been a much better situation.
