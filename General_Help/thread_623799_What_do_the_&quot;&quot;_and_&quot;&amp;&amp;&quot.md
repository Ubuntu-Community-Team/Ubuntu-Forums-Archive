---
title: "What do the &quot;|&quot; and &quot;&amp;&amp;&quot; characters mean?"
date: 2007-11-26
forum: General Help
---

### Post by enchance on 2007-11-26
How does using "|" and "&&" work? I see it a lot but have no idea what it's for. Samples include
```
$ history | grep "foo"
$ wget http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg -O- | sudo apt-key add - && sudo apt-get update
$ wget http://mirror.ubuntulinux.nl/1135D466.gpg -O- | sudo apt-key add -

```
How does it affect the code I type in the terminal? And how come the last example has a "-" in the end?

---

### Post by -grubby on 2007-11-26
I don't know about the pipe character (|) but the && allows you to type more than one command at a time

---

### Post by pebo on 2007-11-26
The pipe sends the output of one command to the input of another - so in the first example the output of 'history' is piped to the input of the 'grep' command.
Not sure about the '-' though...

---

### Post by dpar on 2007-11-26
Google found this....
> Name  	
&& (logical AND)
Examples 	
example pic

for(int i=5; i<=95; i+=5) {
  if((i > 35) && (i < 60)) {
    stroke(0);    //Set color to black
  } else {
    stroke(255);  //Set color to white
  }
  line(30, i, 80, i);
}

Description 	Compares two expressions and returns true only if both evaluate to true. Returns false if one or both evaluate to false. The following list shows all possible combinations:

true && false // Evaluates false because the second is false
false && true // Evaluates false because the first is false
true && true // Evaluates true because both are true
false && false // Evaluates false because both are false
Syntax 	

expression1 && expression2

Parameters 	
expression1 	any valid expression
expression2 	any valid expression
Usage 	Web & Application
Related 	|| (logical OR)
! (logical NOT)
if()

---

### Post by jespdj on 2007-11-26
> **dpar said:**
> Google found this....
But it is not relevant for what the OP is asking...
In programming languages like C, C++ and Java && is the logical AND operator.
But it's not the same for shell script programming and command lines.

---

### Post by geirha on 2007-11-26
command1 && command2 means that command2 will run if, and only if, command1 succeeds (i.e. returns 0).

The | is as pebo explained it

The - in "sudo apt-key add -" is specific to each command. You usually run it as "sudo apt-key add keyfile", but with the -, the command reads the key from standard input instead of a regular file.
```
wget http://mirror.ubuntulinux.nl/1135D466.gpg -O- | sudo apt-key add -
```
is just a shorter way of doing:
```
wget http://mirror.ubuntulinux.nl/1135D466.gpg
sudo apt-key add 1135D466.gpg
rm 1135D466.gpg
```

---

### Post by AlanRogers on 2007-11-26
[Linux Command]("http://www.linuxcommand.org/")

---

### Post by enchance on 2007-11-26
> **AlanRogers said:**
> [Linux Command]("http://www.linuxcommand.org/")
Thanks for your replies. This is a great resource for people like me! I've already gotten my hands dirty with the terminal but as you can see by this post, it's not that dirty enough.:lolflag:

---

### Post by erfahren on 2007-11-26
that was a good question, I wondered about the && as well

this tutorial is good too: [http://www.linux.org/lessons/index.html](http://www.linux.org/lessons/index.html)

---

### Post by enchance on 2007-11-26
> **AlanRogers said:**
> [Linux Command]("http://www.linuxcommand.org/")

Is it possible to get a PDF version of this site or maybe a tar of the whole site? This is great stuff!!

---

### Post by pelle.k on 2007-11-26
The "pipe" is very useful. You use it to glue command together, and thus do some filtering etc. Take "lspci" command; it'll give you a rather large list with devices attached to your pci bus. Say you wan't to see only stuff about your onboard audio.

First with "lspci"
```
pelle@pelle-desktop:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 14)
04:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
05:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
```

Then with "lspci and grep" (grep is a search tool);
```
pelle@pelle-desktop:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

Now with " lspci, grep and conditional echo"

```
pelle@pelle-desktop:~$ lspci | grep Audio && echo i found the found audio controller!
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
i found the found audio controller!

```

There's much more to learn though! :)

---

### Post by dpar on 2007-11-26
> **jespdj said:**
> But it is not relevant for what the OP is asking...
In programming languages like C, C++ and Java && is the logical AND operator.
But it's not the same for shell script programming and command lines.

Could you give me an example? Everything I have found regarding shell scripts or command lines support the logical and function.

---

### Post by enchance on 2007-11-26
> **pelle.k said:**
> 

Now with " lspci, grep and conditional echo"

```
pelle@pelle-desktop:~$ lspci | grep Audio && echo i found the found audio controller!
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
i found the found audio controller!

```

There's much more to learn though! :)

This is great! Is is possible to put the echo at the beginning of the line? Like When I run
```
$ ls -cR ~/MP3/ > ~/Desktop/songlist.txt
```
How do I add a string on top of the txt file like "My songlist" or the date perhaps?

---

### Post by pelle.k on 2007-11-27
Well, the most obvious would be to echo it before the listing...

```
echo My songlist $(date) > ~/Desktop/songlist.txt; ls -cR ~/MP3/ >> ~/Desktop/songlist.txt
```

The "$()" lets you run commands inside it, and present the output as "real text". The ";" is just like return/enter in a terminal (lets you stack command on *one* line). The ">" means put to new file, the ">>" is add to existing file.
[edit]cool huh? :) [/edit]

---

### Post by enchance on 2007-11-27
> **pelle.k said:**
> 
The "$()" lets you run commands inside it, and present the output as "real text". The ";" is just like return/enter in a terminal (lets you stack command on *one* line). The ">" means put to new file, the ">>" is add to existing file.
[edit]cool huh? :) [/edit]

Hehehe, cool. This has got to be the thread where I learn something the most. But can I also use escape characters?

---

### Post by pelle.k on 2007-11-27
Do you mean escape like "\n" for newline etc? Then yes (with "echo -e"). But you need to enclose the text in double qoutes, like this;
```
pelle@pelle-desktop:~$ echo -e "My song list\nDate: $(date)\n"; echo listing goes here...
My song list
Date: Tue Nov 27 18:44:23 CET 2007

listing goes here...

```

Remember, you can always "man <command>" for the basics.

---

### Post by enchance on 2007-11-27
> **pelle.k said:**
> 
Remember, you can always "man <command>" for the basics.

I know, but I always find it more helpful when someone tells me how it's done. You've been very helpful, thank you. Honestly, the man pages are like talking to a brick wall. :lolflag:

---

### Post by pelle.k on 2007-11-27
I just wanted to let you know, in case you didn't already.
Of course I'll be happy to answer any question you might have enchance! :)

---

### Post by enchance on 2007-11-27
I have another question, how do I ls a folder where it shows all the directories first followed by all the files arranged by the same type? I know by now that ls -d isn't the right thing for it.

---

### Post by bodhi.zazen on 2007-11-28
You can set an function in .bashrc :

> function ld { ls -FC --color=always "$@" | grep / | sed -e 's_/__g'; ls -FC --color=always "$@" | grep -v / | sed -e 's_@__g'; }

Then just enter ld

ld <directory to list> 

ie 

ld / 

or

ld /etc

---

