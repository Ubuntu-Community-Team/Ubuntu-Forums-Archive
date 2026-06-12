---
title: "Limewire/Frostwire problems."
date: 2006-11-15
forum: General Help
---

### Post by pyrokinetic on 2006-11-15
Hi there people, 

I've done some searching through the forums here and other places and noticed that plenty of people have been having trouble with Limewire/Frostwire, I seem to be having the same kind of problems as a lot of people (in regards to the window not opening when clicked) but it's a little different for me. I'm running Ubuntu Dapper, I BELIEVE I have the latest version of the java runtime environment (I did the sudo apt-get install sun-java-5plugin or whatever the code was..) but when I try and open limewire or frostwire from the terminal I get this message..

pyrokinetic@pyrokinetic:~$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)

I also get the same message when I try and open frostwire in the terminal too, nor does it work if I click on the icon......not quite sure what's going on with that, does anyone have any tips for me? sorry if this has been posted about before, I couldn't seem to find anything exactly the same as my problem.

---

### Post by acracker on 2006-11-18
I had the same problem too with Limewire and Frostwire. I already had installed Java version 1.5.0_08-b03 but this didn't work. What I did was, at the top of the Gnome desktop click on System, Administration, Synaptic Package Manager. Then I clicked search at the top and typed in java and pressed search. I selected the following packages for installation:

j2re1.4
java-common (if it wasn't already installed)
jre

After I clicked Apply and installed the packages, Frostwire and Limewire booted up fine, with no blank window.

I hope that helps.

---

### Post by gjtoth on 2006-11-18
There was a post that stated if you download the LimewireOTHER.zip (or something like that), extract it, and execute the script runLime.sh it would work perfectly.  And, indeed, after trying his advice, it does.

Hope this helps.

---

