---
title: "Installing Sphinx 4"
date: 2007-09-26
forum: General Help
---

### Post by lexen on 2007-09-26
Hello all, I am trying to get some speech recognition.  I know that it is slim pickings, but I would like to work with whatever is out there and try to make it better.  From what I can tell, the best available is Sphinx 4, but it doesn't come with the ubuntu repository and I am terrible with installing from source.  You can get the source from [_here_]("http://sourceforge.net/project/showfiles.php?group_id=1904&package_id=117949"), but I haven't had any luck.

     It runs in Java, which I think makes it a little harder then most, but I am told it is still do-able.



Thanks,
Lexen

---

### Post by lexen on 2007-10-02
Does anyone know of another speech recognition program that they do know how to install?  I would be much obliged.


Thank you,
Lexen

---

### Post by jlouwerse on 2007-10-03
Any luck yet? I'm trying to do the same.

Greetings
                    Jaco

---

### Post by lexen on 2007-10-03
I found out that you need to compile it using a program called Eclipse, which you can install from synaptic without any trouble.  They have a tutorial [here]("http://cmusphinx.sourceforge.net/sphinx4/doc/Eclipse.html") which explains how to get it to work, but it didn't work for me.  I got somewhere, but not all the way.  The end result was a .jar file.  I tried to run the jar file, but it acted more like a .zip then it did like a .deb.  If anyone knows how to take the next step, or could outright tell me how to compile source code with Eclipse, then we might have a shot.  Until then, I'm stuck.

I feel I should mention that someone has successfully done this with ubuntu.  I asked him how he did it, but he hasn't gotten back to me yet.


Thanks for asking,
Lexen

---

### Post by jlukescott on 2007-10-04
Lexen, the .jar file is something that gets deployed by a java machine, kind of like a web server deploys a bunch of php files and creates a website out of them. I imagine inside of Eclipse, there is going to be a way to open your .jar file, then either run it from inside eclipse or something to that effect. 

Normally, a .jar is a standalone thing that only requires a java engine (which you would invoke by typing "java -jar [sphinx .jar file]" ) - but because you mentioned the Eclipse dependency, there might be some other files/libraries it depends on. This is where my knowledge falls short.

I am trying to install sphinx also, so I'll give this a try.

---

### Post by jlukescott on 2007-10-04
Lexen, try this:
  sudo apt-get install sphinx2-bin
I'm trying to figure out how to do more than just the "test" mode... give it a shot and let me know what you find.
Luke

---

### Post by lexen on 2007-10-06
Alright, I have some good news to report.  Thanks to jlukescott, I installed sphinx2 from synaptic.  I enabled Universal and Multiversal repositories, then installed the program sphinx2-bin.  To run it you have to type sphinx2-demo in the terminal and then you get to play with it.  I actually got to talk and have text appear on screen which is a big step for me.  Unfortunately, it really stinks.  It barely recognized anything that I said and I was very disappointed.  I read in the terminal text that the dictionary it uses is at /usr/share/sphinx2/model/lm/turtle/turtle.dic and if you have root privileges, you can modify it with the following command:

sudo gedit /usr/share/sphinx2/model/lm/turtle/turtle.dic

The dictionary is pretty easy to understand, it has the word that it will type followed by a phonetic version of the word which is what the program actually looks for.  Here are a few examples:

ZONE                 Z OW N
YOU                  Y UW
WRITE                R AY T

In the original text file the second column lined up, but you get the idea.  When I took a look at the dictionary file, it barely had any words in it, which I imagine is because they mentioned that the more words there are in the dictionary the slower the program runs and I think they want it running as fast as possible.

If you want power instead of speed, I found a dictionary for Sphinx that has a lot of words in it.  You can view it [_here_]("http://xvoice-sphinx.sourceforge.net/full.dic.gz").  I feel I should warn you that when I added the words to my dictionary, it didn't seem to make it recognize my speech any better, it just made it so when I talked a wider variety of random words show up on the screen.

That is all I've got.  I once again have to thank jlukescott for helping me get to where I am now.  If anyone has any problems getting to this point, let me know and I will be more then happy to help you out.



Thanks everyone,
Lexen

---

### Post by lexen on 2007-11-06
Alright, I know it's been a while, but I figured something out.  There is actually a program in the gutsy repositories (though I think you need to enable "universal" repositories) for controlling the desktop with voice.  All you need to do is start up synaptic and install "gnome-voice-control" and it will ask you to install sphinx2 and some other stuff.

To start the program, click on the gnome panel (I would suggest the one on top) and click "add to panel."  Scroll down to the miscellaneous section and you should have a new option, "VoiceControl."  If you add that, you will have a light gray triangle added to your panel and it should say idle.  Right click it and say "start control" and speak away.

The program is still at version 0.2 and it shows.  It doesn't understand a lot, but the commands that I got working are:

"close window"
"next window"
"run terminal"

I don't really know my options other then those, and if someone can find a list of commands for this program, that would help me out a ton.

If you want to make this program better, you can submit you voice and help to make the voice recognition more accurate.  All you need to do is go to:

[http://voxforge.org/home/read](http://voxforge.org/home/read)

They have a java program where you press record, read a line and then press stop.  When you do this for all ten lines you press "upload" and send it in so they can process the audio.  You will need java, but think we should all send in our voice to make this program the best it can be.


Thanks,
Lexen

---

### Post by thingmaker on 2007-11-15
Lexen, 

Have you tried Sphinx 4 lately?  Last night I put it on an xubuntu 7.04 box that had jdk1.5.0_01 on it and it went in and ran without incident.  You do not have to compile it with eclipse if you grab the -bin.zip version, only if you get the -src.zip version. 

As I was allready using jdk1.5 as my default java all I did to get sphinx4 running was:

- Do an apt-get install ant
- unzip the sphinx4 bin.zip file
- set up the licence as instructed at [http://cmusphinx.sourceforge.net/sphinx4/doc/jsapi_setup.html]("http://cmusphinx.sourceforge.net/sphinx4/doc/jsapi_setup.html")

and then run the demo programs.

The only "gotcha" was that I tried to run the first demo before I had  looked at the included docs so I did not know to add -mx312m  option to the java -jar command to increase my default java heap space.

Once I did that all included demos ran nicely.

Hope this helps,

-Greg

---

### Post by moonkuh on 2007-11-21
Hi

I tried to setup the license, but i only get an error message. 

x - creating lock directory
x - extracting jsapi.jar (binary)
./jsapi.sh: 1428: uudecode: not found
restore of jsapi.jar failed
./jsapi.sh: 1428: cannot open jsapi.jar: No such file
jsapi.jar: original size 51811, current size !

What can I do?

---

### Post by Mr Green on 2007-11-25
Install the sharutils package.

---

### Post by PacManSPC on 2008-01-22
I have the following setup.

intel quad core processor
4 gig ram
centoOS 5

I have a voicemail system that saves wav files to the server.  I am interested in having these .wav files converted to text and have that text saved in a mysql database.  

With all of that said, has anyone had any success with Sphinx4, and if so, do you think this request is possible?  Is anyone willing to offer me some advice?

Thanks in advance!

---

### Post by foxy123 on 2008-02-20
I've got this trying to run the first demo:
```
~$ java -mx256m -jar bin/HelloWorld.jar
Loading...
10:02.383 SEVERE microphone         couldn't find suitable target audio format
                   in edu.cmu.sphinx.frontend.util.Microphone:initialize-microphone
GC Warning: Out of Memory!  Returning NIL!
GC Warning: Out of Memory!  Returning NIL!
GC Warning: Out of Memory!  Returning NIL!
*** Catastrophic failure while handling uncaught exception.
GC Warning: Out of Memory!  Returning NIL!

```

What is wrong?

EDIT: OK, I've figured it out. Should've set Sun Java in  sudo update-alternatives --config java

---

### Post by u007 on 2008-06-13
uudecode is available under package sharutils :)

---

