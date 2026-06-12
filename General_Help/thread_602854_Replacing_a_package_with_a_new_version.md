---
title: "Replacing a package with a new version"
date: 2007-11-04
forum: General Help
---

### Post by EchoBeach on 2007-11-04
I have installed DOSBox 0.63, using apt-get, on my Ubuntu 6.06 installation.
```
sudo apt-get install dosbox
```I am attempting to get the old DOS game 'Worms United' working, but the DOSBox website suggests I should be using version 0.72.
What resources do I need / procedures do I need to follow in order to successfully upgrade?
I have downloaded the 0.72 source - as I cannot find an appropriate package.
Do I just uninstall the (0.63) package and then create the 0.72 from scratch?
(feeling unsure)
Echo

---

### Post by Maestro23 on 2007-11-04
> **EchoBeach said:**
> I have installed DOSBox 0.63, using apt-get, on my Ubuntu 6.06 installation.
```
sudo apt-get install dosbox
```I am attempting to get the old DOS game 'Worms United' working, but the DOSBox website suggests I should be using version 0.72.
What resources do I need / procedures do I need to follow in order to successfully upgrade?
I have downloaded the 0.72 source - as I cannot find an appropriate package.
Do I just uninstall the (0.63) package and then create the 0.72 from scratch?
(feeling unsure)
Echo

Uninstall the old version using Synpatic.  Then install your new version.  When you extract the tar file, it should have a README/INSTALL doc in it with instructions, required dependencies, etc...

Don't know how to compile from source, read the following link: [http://www.psychocats.net/ubuntu/installingsoftware#source](http://www.psychocats.net/ubuntu/installingsoftware#source)

Good luck.

---

### Post by EchoBeach on 2007-11-06
Thanks for your reply, Maestro23.
I have removed the dosbox 0.63 package and I am now in a dependency chain!
I have typed './configure' in the 'dosbox 0.72' directory and it tells me it can't find SDL.  
When I do the same with 'SDL 1.2.12', it tells me it can't find 'ESD'.
With 'ESD 0.2.38' I'm told two things are missing - 'ARTS' and 'audiofile'.
In 'arts 1.5.8', I get the message: > checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
In 'audiofile 0.2.6', I get the message: > checking for C compiler default output... configure: error: C compiler cannot create executables

As you might have guessed, I am new to this 'compiling from source' lark.

Help, Guidance, please!

Echo

---

### Post by Maestro23 on 2007-11-06
> **EchoBeach said:**
> Thanks for your reply, Maestro23.
I have removed the 0.63 package and I am now in a dependency chain!
dosbox 0.72 -> SDL 1.2.12 -> ESD 0.2.38 ->
arts 1.5.8 -> message: checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
audiofile 0.2.6 -> message: checking for C compiler default output... configure: error: C compiler cannot create executables

As you might have guessed, I am new to this 'compiling from source' lark.

Help!

Echo

Try this to satisfy the dependencies.  In a terminal:

> sudo apt-get build-dep dosbox

Should download any dependencies for dosbox from the repositories.  Then try your compiling from source again.

---

### Post by hamsteroid on 2007-11-10
That's interesting - I did install Dosbox 0.72 in Mandriva 2006.1 during the week and yes there was a train of dependencies starting with SDL. I had also a bit of bother getting a hold of the mesa lib installed (as dosbox compilation was looking for include/SDL/GL/glu.h (as much as I can recall). Finally worked.

The packages make the job much easier - what's interesting here - is that I assumed wrongly that SDL would be installed after installing the dosbox package. ie, when you removed the dosbox package - it removed SDL as well? The **sudo apt-get build-dep dosbox** dep option is pretty cool :)

---

### Post by Maestro23 on 2007-11-10
> **hamsteroid said:**
> That's interesting - I did install Dosbox 0.72 in Mandriva 2006.1 during the week and yes there was a train of dependencies starting with SDL. I had also a bit of bother getting a hold of the mesa lib installed (as dosbox compilation was looking for include/SDL/GL/glu.h (as much as I can recall). Finally worked.

The packages make the job much easier - what's interesting here - is that I assumed wrongly that SDL would be installed after installing the dosbox package. ie, when you removed the dosbox package - it removed SDL as well? The **sudo apt-get build-dep dosbox** dep option is pretty cool :)

Yeah, I discovered the** apt-get build-dep** option when I was digging thru the **man pages** for **apt-get**.

Amazing some of the things you can find.:)

---

### Post by EchoBeach on 2007-11-11
Having used 'sudo apt-get build-dep dosbox', I now have dosbox 0.72 installed and working.
I have managed to get my 'Worms United' installed and running.
At the moment, there's no sound through the onboard sound - the terminal from where I execute the dosbox command talks about not finding a sound directory (I don't have the details  to hand to post them here).
The other thing I now need to experiment with is the assortment of (dosbox) program settings - in order to get the game to run more smoothly.
Echo

---

