---
title: "Installing the Things Necessary to &quot;make&quot; a Program..."
date: 2007-07-06
forum: General Help
---

### Post by qrprat77 on 2007-07-06
Hello,
This is a question about getting to the point where I can "make" a program from the source code.  I just installed Ubuntu 6.06LTS on a computer my dad owns.  We wanted it to get on the internet via a WUSB11v3.0  To do that we needed ndiswrapper, which I suppose, does not come with 6.06.  So, whipping out my trusty memstick, I downloaded the source, untarred it, and promptly found out that typing make at the place I am supposed to type make produces the "bash:  command not found" error. 
After thwacking my forehead in frustration, I remembered something about something needing to be done first.  What does my pop need to install before he can "make" ndiswrapper work??

---

### Post by kevinlyfellow on 2007-07-06
Bash not found??  That sucks!  I don't know why it would say that, but you can make sure that all the dependencies are satisfied
```
sudo apt-get build-dep $PROGRAM
```

---

### Post by lisati on 2007-07-06
I think the message "BASH: COMMAND NOT FOUND" refers here to BASH not being able to make sense of what was typed in - I've had it myself when I've had dyslexic fingers which typed the wrong thing in.

I don't know about 6.06, but 7.04 comes with GCC and a bunch of support utilities pretty much ready to go.

---

### Post by ramjet_1953 on 2007-07-06
Have you installed the [COLOR="Blue"]build-essential [/COLOR]package?

[COLOR="Red"]sudo apt-get install build-essential[/COLOR]

Also, I find [COLOR="Blue"]checkinstall [/COLOR]great to use instead of the [COLOR="Blue"]make install[/COLOR] command, as it produces a deb package for you.

[COLOR="Red"]sudo apt-get install checkinstall[/COLOR]

remember the steps

.[COLOR="Red"]/configure
make
sudo make install (or checkinstall)[/COLOR]

Also you will almost certainly need to satisfy dependencies.

Regards,
Roger :cool:

---

### Post by qrprat77 on 2007-07-06
> **ramjet_1953 said:**
> Have you installed the [COLOR="Blue"]build-essential [/COLOR]package?

[COLOR="Red"]sudo apt-get install build-essential[/COLOR]

Also, I find [COLOR="Blue"]checkinstall [/COLOR]great to use instead of the [COLOR="Blue"]make install[/COLOR] command, as it produces a deb package for you.

[COLOR="Red"]sudo apt-get install checkinstall[/COLOR]

remember the steps

.[COLOR="Red"]/configure
make
sudo make install (or checkinstall)[/COLOR]

Also you will almost certainly need to satisfy dependencies.

Regards,
Roger :cool:

Thanks for the reply guys!  Now does the apt-get command require a net connection??  Cause there ain't none right now....
If it does, what are the necessary things to download and hop over via a memory stick?
Thanks again!

---

### Post by MCSE_Crossover on 2007-07-06
it does require one unless you have the Ubuntu DVD. If you have the DVD, the build-essential pack is located on the disk and you can add the DVD via Synaptic as a package source.

Otherwise, here is the link to the build-essential information and what other packages you are goin to need as dependencies.

[http://packages.ubuntu.com/feisty/devel/build-essential](http://packages.ubuntu.com/feisty/devel/build-essential)

Hope that helps. Best bet, download the Ubuntu DVD. You will eliminate a lot of frustration if your dad doesn't have an internet connection.

---

### Post by kevinlyfellow on 2007-07-06
If your use Synaptic, it can make a script that will download all the programs needed, you only need to have a linux/unix computer with an internet connection somewhere.  In synaptic, its under "File -> Generate Autodownload Script"

---

### Post by qrprat77 on 2007-07-09
> **kevinlyfellow said:**
> If your use Synaptic, it can make a script that will download all the programs needed, you only need to have a linux/unix computer with an internet connection somewhere.  In synaptic, its under "File -> Generate Autodownload Script"

This may be the best option for everything...
One last question I suppose, is it possible to do this running the "Live" cd?  Dad has other computers but they are running *dows.  

Thanks again for the helpful information guys, ya'll rock!!

---

### Post by kevinlyfellow on 2007-07-09
> **qrprat77 said:**
> This may be the best option for everything...
One last question I suppose, is it possible to do this running the "Live" cd?  Dad has other computers but they are running *dows.  

Thanks again for the helpful information guys, ya'll rock!!

Yes, you can do this running on a livecd.  You can also do the downloading on a live cd, provided you have enough memory.

---

### Post by qrprat77 on 2007-07-13
(*bump*)Hey Guys, I think we've almost got this solved.  My dad said he understands what needs to be done, just a matter of finding a little time to do it.

Kevinly:  I'll follow your sig advice soon ;-)

---

### Post by kevinlyfellow on 2007-07-13
> **qrprat77 said:**
> (*bump*)Hey Guys, I think we've almost got this solved.  My dad said he understands what needs to be done, just a matter of finding a little time to do it.

Kevinly:  I'll follow your sig advice soon ;-)

Excellent!  I'm really surprised at how much that the signature advice works!  I saw people doing it on the Arch Linux forums, I though it would be a great thing to do on these forums as well.

Best of luck and keep us informed :-)

---

