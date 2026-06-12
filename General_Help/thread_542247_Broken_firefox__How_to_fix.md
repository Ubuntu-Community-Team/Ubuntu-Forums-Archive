---
title: "Broken firefox ? How to fix ?"
date: 2007-09-03
forum: General Help
---

### Post by cyberfunk on 2007-09-03
Dear users, I seem to have broken firefox on a fresh install of Ubuntu.  The very last thing that I did was to "start new session" after I had rebooted my machine when it game me the option of restore/new session.  Ever since i've been unable to use firefox on either my main account, the root account, or other accounts.

Here's what happens when i try to start firefox by clicking the default button in the GNOME toolbar:  I see a "Starting Firefox Web Browser" appear in my taskbar, and the rotating "Wait" cursor come up.  This persists for ~ 15 seconds, and then the task disappears from the taskbar, and nothing else happens.


I've tried uninstalling firefox and related packages and reinstalling with Synaptic and apt-get, but I still have the same problem.  I've looked in the system logs, but can find no obvious references to firefox.

Has anyone experienced this problem ?  I have no idea what I could have done to cause it... but I'd really like to get my web browsing back !! (Writing this on another computer)

---

### Post by taurus on 2007-09-03
Run it from a terminal to see exactly what's the error message is.

Applications -> Accessories -> Terminal
```
firefox
```

p.s.  Which release are you using right now:  Feisty, Edgy, Dapper, etc.?

---

### Post by cyberfunk on 2007-09-03
Release: Feisty Fawn.

Here's the very strange thing... I DID run it from the terminal and I got absolutely no output, just another prompt, as if I ran a program that did nothing.

P.S.... I'm not sure if this is relevant, but when I installed Epiphany as an alternate browser I got the following message on opening the default page:
"File &#8220;/usr/share/ubuntu-artwork/home/locales/index-C.html&#8221; not found."

---

### Post by taurus on 2007-09-03
And since it's a fresh install, I don't suppose you have anything important (bookmarks and links) that you need to save in ~/.mozilla?  Try to remove that directory and start firefox again from a terminal and see what happens now.

```
rm -rf .mozilla
firefox
```

---

### Post by cyberfunk on 2007-09-03
> **taurus said:**
> And since it's a fresh install, I don't suppose you have anything important (bookmarks and links) that you need to save in ~/.mozilla?  Try to remove that directory and start firefox again from a terminal and see what happens now.

```
rm -rf .mozilla
firefox
```

Ah, I thought of this too, and I tried it.. and again, no result !  It's a very strange problem indeed.


Something to note:  When I type firefox in my terminal, absolutely nothing at all happens... however, when I click the button in GNOME, it "tries" to launch and I see the "Starting Firefox" tab in the task bar temporarily.

---

### Post by cyberfunk on 2007-09-03
Does anyone know where does firefox output it's error log ?  Does it ?  Is there a way to force debug mode ?

P.S.     $ firefox -v DOES print the following line

Mozilla Firefox 2.0.0.6, Copyright (c) 1998 - 2007 mozilla.org

---

### Post by cyberfunk on 2007-09-03
I think I may be getting warmer.... I executed firefox-bin "manually" (instead of via the "firefox" facade executable):

```
 $/usr/lib/firefox/firefox-bin 
```

and got the following output:

/usr/lib/firefox/firefox-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

Any idea on how to fix this guys ?

---

### Post by taurus on 2007-09-03
Here is what you can do.  Download firefox from [http://www.mozilla.com/en-US/](http://www.mozilla.com/en-US/) and unpack it somewhere in your $HOME directory.  Then, see if it comes with libmozjs.so.  Just copy it to /usr/lib and see if firefox (/usr/lib/firefox/firefox-bin) starts now.

---

### Post by cyberfunk on 2007-09-03
Ugh... this problem seems to be getting just worse and worse.... this is remeniscent of a problem I had when I tried to install Ubunutu the first time, where the OS wouldnt see files that are right in front of it !!


I downloaded firefox and ran the following:: ./firefox  and it told me

./run-mozilla.sh: 424: ./firefox-bin: not found

despite the firefox-bin clearly being in the same folder.  When I tried to run the firefox-bin in the same folder ( ./firefox-bin) I get the following output:  

bash: ./firefox-bin: No such file or directory

Last time I had this problem (the not-finding things right in front of you one) I had to reinstall all of Ubuntu to make it go away !  Please say it isnt so ??

What could I have possibly have done to trigger this behavior?  I've tried rebooting several times, btw.

Note: I've noticed that this problem is now occuring with OTHER programs on my system !!  There are several programs I can't run because I'm told that the file can't be found.  I've clearly made some system-wide change to bring this evil system-wide symptom back!  I think i'll go nuts if I have to reinstall for the 4th time !

Has anyone ever experienced this very strange behavior before ?  Is there any remedy besides a reinstall ?  what should I do to avoid triggering this "filesystem disease" in the future?  I'm really desperate at this point not to reinstall this.. i've finally got everything installed and working.. until this happened.


P.S.  Sorry if it sounds like i've lost my mind here, but installing Ubuntu should not be this hard!  I think among the ATI driver problems and these random "I don't feel like working anymore" errors, this is sheer madness.  I'd be infinitely greatfull to someone who knows how to fix this "invisible" file problem.

---

### Post by cyberfunk on 2007-09-03
Since this problem is no longer really a firefox problem, I decided to repost it as: [http://ubuntuforums.org/showthread.php?t=542315](http://ubuntuforums.org/showthread.php?t=542315)

Hopefully someone really smart can help me with this very frustrating issue.

---

### Post by firstone on 2007-09-06
I am a new Linux/Ubuntu user and I am having the same problem with Dynamips Cisco emulator. Although the install was fine and all files are there I get the "bash: /usr/local/bin/dynamips: No such file or directory" message.

Any help would be appreciated...Thanks

---

