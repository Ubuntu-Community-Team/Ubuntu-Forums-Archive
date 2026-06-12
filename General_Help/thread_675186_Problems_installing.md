---
title: "Problems installing"
date: 2008-01-22
forum: General Help
---

### Post by Sam Throssell on 2008-01-22
I searched but i couldnt find anything

i get this message when i try to install a program

only one software management tool is allowed to run at the same time
please close the other application eg update manager, aptitude or synaptic first

i dont know what this means can anyone help me?

---

### Post by silviur on 2008-01-22
That means you have another installer-program running already, like Update Manager, Synaptic or the Terminal "sudo apt-get install".
 Let the other programs finish and then do your thing.
 You can also restart (if one of these programs stopped responding and it's still "running").

---

### Post by Sam Throssell on 2008-01-22
its been like this for 2 months+ m8

---

### Post by djrobthaman on 2008-01-22
> **silviur said:**
> That means you have another installer-program running already, like Update Manager, Synaptic or the Terminal "sudo apt-get install".
 Let the other programs finish and then do your thing.

What he said

---

### Post by silviur on 2008-01-22
Go to administration, then System Monitor, then select in the list the installer program that is running and choose End process (that will kill it). Then install your program.

---

### Post by Sam Throssell on 2008-01-22
thats what i dont understand i dont know which tab to open up and i cant see an installer program running 

im not very good with computers sorry :(

---

### Post by silviur on 2008-01-22
No problem :)

Go to the menu System, then from the submenu choose Administration, then System monitor. When System Monitor opens up, left click from the list the program (update-notifier), and then choose "end process". This will stop that installer and then you can install your program. 
This is a temporary measure, until you restart the system.

---

### Post by Sam Throssell on 2008-01-22
m8 i still have the problem :( and i ended that task

---

### Post by silviur on 2008-01-22
.

---

### Post by Sam Throssell on 2008-01-22
i cant see the links when i copy and paste them into my browser

do u use msn or aim? it would be a little bit easier talking there

---

### Post by silviur on 2008-01-22
No, I made some screenshots of the previous operations, which you already did, and the forum didn't show them for some reason.

If you found that program and "End process"-ed it, then is another program still "running".

Go to System-Preferences-Sessions, and deselect the programs which might be update managers or packet managers (they should have a similar name).

---

### Post by Sam Throssell on 2008-01-22
i deleted the update manager thing but i dont see anthing else

and it still has the problem :(

---

### Post by silviur on 2008-01-22
I'm sorry Sam, this is all I know at this time, I use Ubuntu only for 6 months.
But be patient, there are a lot of guys who know more and are willing to help you, just wait for more responders :)

---

### Post by djrobthaman on 2008-01-22
Sam, what windows do you have open when you try to install anything?

---

### Post by Sam Throssell on 2008-01-22
thanks sil for ur help!

the wondows i have open well just my browser

---

### Post by moshos on 2008-01-22
In terminal type this:

sudo apt-get update

And if dosn't work type this before:

 dpkg --configure -a


I hade exact the same problem, and i restarted the computer about 6 times,, read this forum, and finded a solution,,,i think this happends when broken packages is deliveried.

Have fun

---

### Post by Sam Throssell on 2008-01-23
what is terminal m8?

---

### Post by Sam Throssell on 2008-01-23
i get this 

sam@sam-desktop:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Fetched 1B in 0s (2B/s)  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
sam@sam-desktop:~$ 


and when i type dpkg --configure -a i get this

sam@sam-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
sam@sam-desktop:~$

---

### Post by silviur on 2008-01-23
do the last command with "sudo" first
```
sudo dpkg --configure -a
```

---

### Post by Sam Throssell on 2008-01-23
ok got this doing that

sam@sam-desktop:~$ sudo dpkg --configure -a
Setting up java-common (0.26ubuntu1) ...

Setting up odbcinst1debian1 (2.2.11-16) ...

Setting up unixodbc (2.2.11-16) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
sam@sam-desktop:~$

---

### Post by Sam Throssell on 2008-01-23
yes! it works w00t

guys thanks so mcuh for your help you guys are great! :D:D

---

### Post by silviur on 2008-01-23
You're welcome Sam :)
Enjoy your Ubuntu, and "thank" us on the right side of the page ;)

---

### Post by Sam Throssell on 2008-01-23
i just restarted my computer cos the download jammed and its happened again >.>

---

### Post by silviur on 2008-01-23
Do ```
sudo apt-get update
``` **and**
```
sudo apt-get upgrade
``` again, with ...reconfigure if its the case.

---

### Post by Sam Throssell on 2008-01-23
ok i got this after doing that

sorry about this :(

sam@sam-desktop:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Fetched 1B in 0s (1B/s)  
Reading package lists... Done
sam@sam-desktop:~$

---

### Post by Sam Throssell on 2008-01-23
then i did the upgrade and i got a window with this

 Configuring sun-java5-bin and lots of writing

---

### Post by silviur on 2008-01-23
Yes, wait until the java thing gets done, I remember it took a lot of time in my case. Let it do its thing for 10 minutes even, if it stops responding then restart. Just wait and see :)

---

### Post by Sam Throssell on 2008-01-23
its not really doing anything its just writing really this is what it says at the top

 Operating System Distributor License for Java v1.1 (DLJ)                  &#8593;  
 &#9474;                                                                           &#9646;  
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618;  
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618;  
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618;  
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618;  
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618;  
 &#9474; TERMS OF THE AGREEMENT.

---

### Post by silviur on 2008-01-23
Try this:

```
 sudo apt-get install  java7-runtime -y

```

---

### Post by Sam Throssell on 2008-01-23
i get this :mad:

sam@sam-desktop:~$ sudo apt-get install  java7-runtime -y
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
sam@sam-desktop:~$

---

### Post by silviur on 2008-01-23
Do ```
sudo dpkg --configure -a
``` and redo the previous steps (forget my java7 command for now). When you get at that text with the license agreement, scroll down with the down key and accept it (maybe pressing Y).

---

### Post by Sam Throssell on 2008-01-23
sam@sam-desktop:~$ sudo dpkg --configure -a
sam@sam-desktop:~$ 

thats all i get when i put that code in though :S

---

### Post by silviur on 2008-01-23
```
sudo apt-get update -f
``` then
```
sudo apt-get upgrade
```.

---

### Post by Sam Throssell on 2008-01-23
ok i did that and i got the configuration writing again and theres nothing i can really do on this page

---

### Post by Sam Throssell on 2008-01-23
i still have the problem m8 :(

---

### Post by silviur on 2008-01-23
.

---

### Post by Sam Throssell on 2008-01-23
i need to go m8 i have college class now ill be back in 3 hours or so

if you have msn add [email]mrsammy@hotmail.co.uk[/email]

or if u use AIM add mrsammy1988

it would be easier for us to talk

---

### Post by silviur on 2008-01-23
Ok, i added you. We'll talk later.

---

### Post by Sam Throssell on 2008-01-23
ok im back m8

---

