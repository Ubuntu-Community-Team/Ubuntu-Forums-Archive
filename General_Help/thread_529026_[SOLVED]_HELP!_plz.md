---
title: "[SOLVED] HELP! plz"
date: 2007-08-18
forum: General Help
---

### Post by crazygun on 2007-08-18
okay here is the deal. my computer wont let me update anything. and i have talked to some other peeps and they told me to open terminal and put dpkg --configure -a.
so i did that and all... and now im lost.
i can't open my synaptic package manager... cuz computer wont let me.
      so now i dont know what to do.
i have my terminal open and im just sitting here. can some one tell me what do i need to do all the way to get my computer to run my updates. i think i have a broken packages and all. so how do i fix that problem too?

---

### Post by walkerk on 2007-08-18
> **crazygun said:**
> okay here is the deal. my computer wont let me update anything. and i have talked to some other peeps and they told me to open terminal and put dpkg --configure -a.
so i did that and all... and now im lost.
i can't open my synaptic package manager... cuz computer wont let me.
      so now i dont know what to do.
i have my terminal open and im just sitting here. can some one tell me what do i need to do all the way to get my computer to run my updates. i think i have a broken packages and all. so how do i fix that problem too?

This will attempt to fix the broken packages.
```
sudo apt-get update -f
```

---

### Post by crazygun on 2007-08-18
okay i put that in..... now what? do i need to do anything else?

---

### Post by crazygun on 2007-08-18
okay i also put in "sudo apt-get install -f" and it locked up my terminal

---

### Post by crazygun on 2007-08-18
okay i put that thing in again and this is what its now saying...

 E: dpkg was interrupted, you must manually run "dpkg --configure -a" to correct the problem.

 okay so i put that in to run it. and this is what it said,

dpkg: requested operation require superuser privilege 

             now what am i going to do? can anyone tell me that?

---

### Post by forestpixie on 2007-08-18
in terminal 

sudo dpkg --configure -a

most commands that allow you to change a system file will need sudo - it will ask for your password - enter it butr be aware that you won't see it at all

---

### Post by g2g591 on 2007-08-18
the main reason you got this message was you interupted when you were running apt-get install -f

---

### Post by crazygun on 2007-08-18
that didnt work... or im putting it in wrong, im not sure. but nothing happened

---

### Post by g2g591 on 2007-08-18
just copy and paste, this : sudo apt-get install -f
if it just shows a flashing cursor (nothing in front of it) that means its still working, once it says your name@yourcomputername:$ then its done

---

### Post by crazygun on 2007-08-18
okay this is what i got now....

its was running but now this is what it said half way through the downloading 

E:/var/cache/apt/archives/sun-java5-bin_1.5.0-11-1ubuntu2_i386.deb:
subprocess pre-installation script returned error exit status 1E:/var/cache/apt/archives/sun-java5-bin_1.5.0-11-1ubuntu2_i386.deb:
subprocess pre-installation script returned error exit status 1

---

### Post by walkerk on 2007-08-18
> **crazygun said:**
> okay this is what i got now....

its was running but now this is what it said half way through the downloading 

E:/var/cache/apt/archives/sun-java5-bin_1.5.0-11-1ubuntu2_i386.deb:
subprocess pre-installation script returned error exit status 1E:/var/cache/apt/archives/sun-java5-bin_1.5.0-11-1ubuntu2_i386.deb:
subprocess pre-installation script returned error exit status 1

try this:
```
cd /var/cache/apt/archive
```

uninstall that package:
```
sudo dpkg -r -P sun-java5-bin_1.5.0-11-1ubuntu2_i386.deb

or

sudo apt-get --purge remove sun-java5-bin
```

remove that deb from the archive:
```
sudo rm sun-java5-bin_1.5.0-11-1ubuntu2_i386.deb
```

re-install it from repository:
```
sudo apt-get update -f

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-fonts
```

that will upgrade you from version 5 to 6. if you want 5 just replace the 6s with 5s.

---

### Post by crazygun on 2007-08-18
is doesn't really matter to me.. i just want this thing to work. thats all im looking for. okay i will try all those codes and i will tell you what happens.

---

### Post by crazygun on 2007-08-18
okay... i try to do it all now it is saying... E:Couldn't find package sun-jajava6-bin

i put in sudo apt-get update -f and it got that part done. 

but when i put in "sudo rm sun-java5_bin_1.5.0-11-1ubuntu2_i368.deb 
it said: rm: cannot remove 'sun-java5_bin_1.5.0-11-1ubuntu2_i368.deb': No such file or directory

so then i put in "sudo apt-get install sum-jajava6-bin sun0java6-jre sub-java6-fonts"

 it said: Reading package lists...Done
              Building dependency tree
              Reading state information...Done
              E: Couldn't find package sun-jajava6-bin 

now what?

---

### Post by walkerk on 2007-08-18
> **crazygun said:**
> okay... i try to do it all now it is saying... E:Couldn't find package sun-jajava6-bin

i put in sudo apt-get update -f and it got that part done. 

but when i put in "sudo rm sun-java5_bin_1.5.0-11-1ubuntu2_i368.deb 
it said: rm: cannot remove 'sun-java5_bin_1.5.0-11-1ubuntu2_i368.deb': No such file or directory

so then i put in "sudo apt-get install sum-jajava6-bin sun0java6-jre sub-java6-fonts"

 it said: Reading package lists...Done
              Building dependency tree
              Reading state information...Done
              E: Couldn't find package sun-jajava6-bin 

now what?

"sudo apt-get install sum-jajava6-bin sun0java6-jre sub-java6-fonts"

ok, copy & paste:
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-fonts
```

---

### Post by crazygun on 2007-08-18
okay that worked! im going to hit yes,... and see what happens

---

### Post by walkerk on 2007-08-18
whats the output of:
```
ls /var/cache/apt/archives | grep sun
```

---

### Post by walkerk on 2007-08-18
did you purge sun-java6-bin? If not do this to get rid of the broken package:
```
sudo apt-get --purge remove sun-java5-bin
```

---

### Post by crazygun on 2007-08-18
okay... it gave me that blue screen thang again... now what. i didnt get to put the other codes in yet before that blue screen popped up.

---

### Post by walkerk on 2007-08-18
> **crazygun said:**
> okay... it gave me that blue screen thang again... now what. i didnt get to put the other codes in yet before that blue screen popped up.

Blue screen?

---

### Post by crazygun on 2007-08-18
it says: Package configuration 

                   Configuring sun-java6-bin

 Operating System Distributor License for Java v1/1 (DLJ) 
 Operating System Distributor License for Java version 1.1 (DLJ) 
 
Sun Microsystems, Inc. ("SUN") is willing to license the Java platform standard edition developed kit...........bla bla bla...

 yeah it keeps going on and on and on. It wont let me do anything but read it. so if i have to put in an other code i have to open a new terminal to do it.

---

### Post by crazygun on 2007-08-18
okay i think i got it now... thanks for all the help  really. i couldn't have done it without everyone and your help.

---

