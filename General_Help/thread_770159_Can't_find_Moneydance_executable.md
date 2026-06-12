---
title: "Can't find Moneydance executable"
date: 2008-04-27
forum: General Help
---

### Post by Island_Jon on 2008-04-27
This is a _re-install_ of the purchased copy after I upgraded the whole Ubuntu to Heron ver. 8.04.

I first installed sun-java6-bin and the recommends.  Then untarred the *Moneydance_linux_x86.tar.gz* (version _WITHOUT_ Java) to the usr/local.  I succeeded in running the shell script Moneydance that is evidently supposed to  install  the program, because there were no errors when this script ran AND _it started Moneydance surccessfully_ and I was able to open my previous Moneydance data file.

BUT now I can't find the executable to start up Moneydance.  I obviously can't run it by clicking on the Moneydance icon .png file.

Where is the executable or am I not finished with the installation?
Thanks for any help
Jon

---

### Post by ewg on 2008-04-27
I've got a similar problem: Moneydance 2007 does not work for me after I upgraded to Ubuntu 8.04. Nothinf happens when i click on the icon or the menu selection. Had no problems with previous upgrades.

---

### Post by Island_Jon on 2008-04-27
Fortunately a kind person, setiraz, helped me:
 
you did not choose the installation bundle! you just unpacked MD, the included script just starts MD - it does not install!
please download MD installation pack
[http://moneydance.com/forum/YaBB.pl?action=dereferer;url=http://moneydance.com/download/2008/installers/moneydance_linux_x86.sh](http://moneydance.com/forum/YaBB.pl?action=dereferer;url=http://moneydance.com/download/2008/installers/moneydance_linux_x86.sh)
 (MD Linux without java) - looks like that one is not listed on download page...

---

### Post by ThymeTraveler on 2008-09-18
I am so confused! :confused: I did like you did because that is exactly what the instructions say to do when I go to the Moneydance DOWNLOAD section.  And the file is only the tar file with extension .gz  The instructions say to extract it and then double click on the icon (which of course does not work since it is only an image).  I can start up Moneydance by clicking on the shell script and actually get into my file.

There is no .sh file for installation that I can find.

So I clicked on the link in your last reply,  *Now what?*  When I double click, I get a message that it is a binary file and that saving it will corrupt it.  Is there a specific command I should use?  I'm just slowly learning Linux (Kubuntu).  This is the first software program (and hopefully ONLY) program that I have to install without using Adept.

Should I be putting a command in the terminal?  If so, could you give me the specific code?:confused:

---

### Post by ewg on 2008-09-20
MY MD problem was caused by a java glitch. When I was directed to the correct version of java, in another forum, my MD worked fine.

---

### Post by ThymeTraveler on 2008-09-20
I solved my problem.  After looking through several books that I acquired about Ubuntu, I discovered the command sh.  Putting sh before the .sh file while in the terminal installed the Moneydance program.  It doesn't show up in Kmenu, but I put the icon on the panel where I keep my other most often used program icons.:KS

---

### Post by wmjpalmerjr on 2008-10-05
Hello,

What was the information about the correct Java release?

Thanks, wm

---

### Post by ewg on 2008-10-05
The complete post that fixed me up is here:

[http://ubuntuforums.org/showthread.php?t=774973&highlight=moneydance](http://ubuntuforums.org/showthread.php?t=774973&highlight=moneydance)

good luck,

---

### Post by wmjpalmerjr on 2008-10-06
Hello again, 

I followed the whole process and Moneydance still comes back

wmjpalmerjr@dell-desktop:~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*+        3    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
wmjpalmerjr@dell-desktop:~$ Moneydance
bash: Moneydance: command not found

Even with a hot reboot.

???????:confused:

---

### Post by wmjpalmerjr on 2008-10-06
hello, when I tried starting via launcher it worked.
BUT, when typing "Moneydance" is shell it still fails.

Thanks, Wm:popcorn:

---

