---
title: "Ubuntu n00b: where to put applications obtained outside of Synaptic/AddRemove?"
date: 2008-02-03
forum: General Help
---

### Post by Bard09 on 2008-02-03
I just switched my laptop over to Ubuntu yesterday and have to say I am thrilled at how easy the rollover was compared to my experiences with Ubuntu several years ago.  Heck, even WINDOWS file-sharing worked with only one tiny tweak.  It even supports my touchpad now, which was absolutely impossible back when.

Very pleased!

Anyways, my question:

One application I'm considering running is Aptana, a pretty high-profile GPL'ed web development app.  The only problem is that I couldn't find it via Synaptic or Add/Remove-- meaning I had to download the .zip (full application) directly from Aptana's website.

Now, given that I'm just a n00b, I'm still pretty lost at the Ubuntu file hierarchy when browsing root.  So my question is: where the heck should I put this thing?

I know it's a dumb question, but considering the other 95% of applications I'll be using on this system will be distributed among the root folders, I'd like to approach Aptana with a similar organizational philosophy.

Advice for my need to organize this rogue application properly?

---

### Post by TheBoat on 2008-02-03
If you type   ```
 echo $PATH
```      in the terminal it will give you all the directories that it currently looks in when you try to execute a program. (Otherwise you will have to give the entire path to the application in order to execute it)  I suggest putting the application in one of those bin directories or creating a new directory and adding to the PATH.

---

### Post by erfahren on 2008-02-03
see: [http://www.aptana.com/docs/index.php/Installing_Aptana_on_Linux](http://www.aptana.com/docs/index.php/Installing_Aptana_on_Linux)

-- for 32-bit Ubuntu
> 
Aptana Milestone 8 installs very easily on Fedora Core 6 or Ubuntu Feisty assuming you have Firefox and Sun JVM 1.5 or higher installed. You should be able to unzip the .zip file to the location of your choice and click on the Aptana executable to get going. More distro-specific instructions will be posted here as necessary.

for 64-bit Ubuntu it looks like there's a little more to it - see the page

---

### Post by Bard09 on 2008-02-03
Thanks, TheBoat!  I'll check that out.  I'm a little concerned about splitting it up, but that might key in some possible locations to put the folder.

@erfahren: I'm actually at that point-- the applications runs; I'm just not sure where to put it.  It might be because I'm using a new OS that it feels like Aptana doesn't have a 'home'.   OCD, much?  :)

---

### Post by erfahren on 2008-02-03
> **Bard09 said:**
> Thanks, TheBoat!  I'll check that out.  I'm a little concerned about splitting it up, but that might key in some possible locations to put the folder.

@erfahren: I'm actually at that point-- the applications runs; I'm just not sure where to put it.  It might be because I'm using a new OS that it feels like Aptana doesn't have a 'home'.   OCD, much?  :)
oh, ok -- actually programs like that you can just put into your home directory somewhere (in a folder named "programs" or whatever)

you can create a launcher to the excutable file by right-clicking on the top panel and for the command put the path to the excutable - like this:
```

/home/Bard09/programs/Aptana/Aptana

```
you could also add an entry in the main menu for it, see: [http://ubuntuforums.org/showthread.php?t=533265](http://ubuntuforums.org/showthread.php?t=533265)

 - you could also put it in "/opt" - that's a good place for you own applications, but you'd need to move it there with root permissions. - if you want to move it there I can tell you what to do

---

### Post by pointone on 2008-02-03
Traditionally, /opt and /usr/local are for this type of thing.

Historically, /opt is for pre-packaged, commercial software, /usr/local for locally compiled.

---

### Post by Bard09 on 2008-02-03
To erfahren & pointone:

Thanks!  I decided to go with /opt-- Aptana is pre-compiled and unzipped into one solid directory.

Do you guys know if there's an Ubuntu/Linux glossary out there that explains the folder hierarchy?   I'm doing swimmingly with the terminal... it's just all the folder names ("etc" "bin" "lib" "sbin" "proc") that confuse me!

---

### Post by pointone on 2008-02-03
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

