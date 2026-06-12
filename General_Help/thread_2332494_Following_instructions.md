---
title: "Following instructions"
date: 2016-08-01
forum: General Help
---

### Post by vader-xanth on 2016-08-01
Hello

I am starting a book which has step by step instructions for doing stuff. Even though I could skip a few non-essential steps, I have to do them all.. I think that I'm starting to get a disorder...

Anyways, I was told to 'sudo apt-get install chromium' and I was given an error.. I will paste the code now:

vader@vader-HP-2000-Notebook-PC:~$ sudo apt-get install chromium
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Package chromium is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
chromium-bsu:i386 chromium-bsu

E: Package 'chromium' has no installation candidate
vader@vader-HP-2000-Notebook-PC:~$ sudo apt-get install chromium-bsu:i386 chromium-bsu
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
chromium-bsu : Conflicts: chromium-bsu:i386 but 0.9.15.1-1 is to be installed
chromium-bsu:i386 : Depends: chromium-bsu-data:i386 (>= 0.9.14) but it is not installable
Depends: libglc0:i386 (>= 0.7.1) but it is not going to be installed
Conflicts: chromium-bsu but 0.9.15.1-1 is to be installed
E: Unable to correct problems, you have held broken packages.
vader@vader-HP-2000-Notebook-PC:~$ 



So here are my questions: 1) do I now have a bunch of useless stuff on my computer (packages there were installed) but no running chromium? and 2) If the answer for #1 was 'True', how do I go about resolving it by either getting it all or getting rid of it all?

Thank you for your time and effort in answering these ?s

---

### Post by dragonfly41 on 2016-08-01
It helps the forum to know what OS you have installed.

Try using command [COLOR=#000000]sudo apt-get install chromium-browser  ... not simply chromium

and you could install Synaptic Package Manager .. which if you use and search "chromium"
you will see what packages are installed.[/COLOR]

---

### Post by sudodus on 2016-08-01
There is the browser Chromium with the package **chromium-browser** and there is the game Chromium with the package **chromium-bsu**, [http://chromium-bsu.en.softonic.com/](http://chromium-bsu.en.softonic.com/)

Which of them do you want?

If it is the game, please search for more information via the internet for example with this search string: **chromium bsu**

If the package **chromium-bsu** is well prepared, it should work in Ubuntu. Maybe it works better in another version of Ubuntu.

---

### Post by vader-xanth on 2016-08-01
> **dragonfly41 said:**
> It helps the forum to know what OS you have installed.

Try using command [COLOR=#000000]sudo apt-get install chromium-browser  ... not simply chromium

and you could install Synaptic Package Manager .. which if you use and search "chromium"
you will see what packages are installed.[/COLOR]

I'm sorry.. I am using Ubuntu 16.04LTS.  Your suggestion of adding the -browser worked.  Thank you!

I do have Synaptic, but I need to get used to the terminal.

Many thanks!!

---

### Post by sudodus on 2016-08-01
Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

It will help other people to find your solution.

---

### Post by vader-xanth on 2016-08-01
> **sudodus said:**
> There is the browser Chromium with the package **chromium-browser** and there is the game Chromium with the package **chromium-bsu**, [http://chromium-bsu.en.softonic.com/](http://chromium-bsu.en.softonic.com/)

Which of them do you want?

If it is the game, please search for more information via the internet for example with this search string: **chromium bsu**

If the package **chromium-bsu** is well prepared, it should work in Ubuntu. Maybe it works better in another version of Ubuntu.

I never thought that one program would have been named so close to another.  My bad for not researching further.  But to answer your question, it was the browser that I was looking for.  It looks like I have more than I thought to learn.

However, thank you for the help! :)

---

### Post by grahammechanical on 2016-08-01
You have learnt that when using the terminal to install software we need an accurate package name. Whereas, a software store will take care of that for us.

You may be interested to know that with Ubuntu 16.04 we can use "apt" instead of "apt-get." For example:

```
sudo apt install chromium-browser
```

[http://manpages.ubuntu.com/manpages/xenial/man8/apt.8.html](http://manpages.ubuntu.com/manpages/xenial/man8/apt.8.html)

Regards

---

