---
title: "Installing Opera"
date: 2005-07-20
forum: General Help
---

### Post by installer on 2005-07-20
Can someone explain please (in very simple terms) how to install Opera (with Java) I have managed to get Opera 8.01 (No Java) up and running.

Please keep it very simple, as I only installed Ubuntu yesterday, and it took me two hours to get Opera installed.

Thanks in advance.

---

### Post by lol on 2005-07-20
Make sure you have a working JDK installed (1.5 preferably), then:

- start Opera
- go in Tools->Preferences, then Advanced->Content
- clic on Java options and enter the path to your java installation (/usr/lib/j2sdk1.5-sun/jre/lib/i386 for example)

You can check that the path is correct with the "Validate path" button. Be carefull, the path have to point to the jre/lib/i386 folder, not to the root of the java installation.

Restart Opera, java should be working. If not, press F12, and make sure that both "Enable Java" and "Enable Javascript" options are checked.

Hope this can help.

---

### Post by installer on 2005-07-20
[QUOTE=lol]Make sure you have a working JDK installed (1.5 preferably), then:

- start Opera
- go in Tools->Preferences, then Advanced->Content
- clic on Java options and enter the path to your java installation (/usr/lib/j2sdk1.5-sun/jre/lib/i386 for example)

You can check that the path is correct with the "Validate path" button. Be carefull, the path have to point to the jre/lib/i386 folder, not to the root of the java installation.

Restart Opera, java should be working. If not, press F12, and make sure that both "Enable Java" and "Enable Javascript" options are checked.

Hope this can help.[/QUOTE]
 I haven't got java installed, how do I do it?

Seems like a nightmare to do, is there an easy explanation anywhere? there doesn't seem to be a method on this site that works for me.

---

### Post by Ramon on 2005-07-20
maby this link : [http://www.ubuntuforums.org/showthread.php?t=22646](http://www.ubuntuforums.org/showthread.php?t=22646) is someting for you.

its easy and simple, donwload the script ans then follow the install rulez down below.  :-P 

Then you get some other stuf as well and java :)

---

### Post by Phixion on 2005-07-20
[QUOTE=installer]I haven't got java installed, how do I do it?

Seems like a nightmare to do, is there an easy explanation anywhere? there doesn't seem to be a method on this site that works for me.[/QUOTE]

[http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre)

thats for installing java, I suggest u follow that guide, it helped me alot :)

---

### Post by installer on 2005-07-20
[QUOTE=Ramon]maby this link : [http://www.ubuntuforums.org/showthread.php?t=22646](http://www.ubuntuforums.org/showthread.php?t=22646) is someting for you.

its easy and simple, donwload the script ans then follow the install rulez down below.  :-P 

Then you get some other stuf as well and java :)[/QUOTE]

Thanks trying this now

---

### Post by installer on 2005-07-20
[QUOTE=Phixion][http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre)

thats for installing java, I suggest u follow that guide, it helped me alot :)[/QUOTE]

Allready tried this didn't work for me, thanks anyway.

---

### Post by installer on 2005-07-20
The method linked to by Ramon worked, plus gave me some other useful goodies thanks.

---

### Post by lol on 2005-07-21
[QUOTE=installer]I haven't got java installed, how do I do it?

Seems like a nightmare to do, is there an easy explanation anywhere? there doesn't seem to be a method on this site that works for me.[/QUOTE]

I know you finally get it installed successfully using the script Ramon suggested, but just to let you know, there is really nothing difficult to do to install Java.

The easy way to do it is to select one of the correct package in synactic (or whichever package managment system you are using).

Right now, you can select between "sun-j2re1.5" or "sun-j2sdk1.5"

The trouble is that those 2 packages are not provided by default in Ubuntu. As far as I know, they are part of what is called the "Backports". It means that you need to add the backports repository in your /etc/apt/sources.list file (this was done automatically by the script you used).

But once this is done, you can install or remove Java just as easilly as any other package.

---

### Post by installer on 2005-07-21
Thaks lol beginning to find my way around Ubuntu, your last post has made it a little clearer for me.  :smile:

---

