---
title: "Getting Novell Groupwise to work in Ubuntu"
date: 2005-07-25
forum: General Help
---

### Post by Zifnab on 2005-07-25
My company uses Novell GroupWise for its email system, and they have convenient little Windows client downloads for use at home. I've since switched to Ubuntu, however, but our web interface for accessing email is rather lacking. (Though certainly decent enough for a web interface, it's no gmail.)

Now Novell decided to go all Linuxy, which is a good thing, and in fact has released a GroupWise for Linux client. *Sweet*, I thought. Well, almost.

It has a little install executable, which in turn just installs an .rpm file. It may do other stuff, I don't really know, but I'm not exactly running Red Hat so it doesn't work in any case.

So I found that Ubuntu has a handy app called alien, with which I converted the .rpm to a more Ubuntu-friendly .deb. So I su'ed and did a "dpkg -i <filename>", and it seemed to install okay. The trouble arose when I found that *I have no idea where the hell it installed it to.* I can remove it fine with "dpkg -r <packagename>", and it tells me it removed several thousand files/directories from *somewhere*, but I have no idea where it is. Nothing useful seems to have been added to /usr/bin or the like either. *sigh*

So I ask for advice in one (or both) of two forms: 
HOWTO install GroupWise in Ubuntu -or-
HOWTO find out where the hell dpkg puts stuff.

Thanks for reading through my iritated rant, and quadruple thanks in advance for any help.  :grin:

---

### Post by damonw5 on 2005-07-25
[QUOTE=Zifnab]My company uses Novell GroupWise for its email system, and they have convenient little Windows client downloads for use at home. I've since switched to Ubuntu, however, but our web interface for accessing email is rather lacking. (Though certainly decent enough for a web interface, it's no gmail.)

Now Novell decided to go all Linuxy, which is a good thing, and in fact has released a GroupWise for Linux client. *Sweet*, I thought. Well, almost.

It has a little install executable, which in turn just installs an .rpm file. It may do other stuff, I don't really know, but I'm not exactly running Red Hat so it doesn't work in any case.

So I found that Ubuntu has a handy app called alien, with which I converted the .rpm to a more Ubuntu-friendly .deb. So I su'ed and did a "dpkg -i <filename>", and it seemed to install okay. The trouble arose when I found that *I have no idea where the hell it installed it to.* I can remove it fine with "dpkg -r <packagename>", and it tells me it removed several thousand files/directories from *somewhere*, but I have no idea where it is. Nothing useful seems to have been added to /usr/bin or the like either. *sigh*

So I ask for advice in one (or both) of two forms: 
HOWTO install GroupWise in Ubuntu -or-
HOWTO find out where the hell dpkg puts stuff.

Thanks for reading through my iritated rant, and quadruple thanks in advance for any help.  :grin:[/QUOTE]
 Just to let you know: Evolution supposedly has support for Groupwise. However, back to your original question:

What happens when you double-click that .deb file? Browse through the files and see if that gives you clues as to where the files are going.

Also, when in doubt, try running /usr/bin/groupwise -- it just might work! :)

---

### Post by Zifnab on 2005-07-26
Evolution does, eh? I'll have to check that out, thanks. Does Thunderbird, btw?

And sadly no, there was no new executable (that I could find) put into /usr/bin or /usr/local/bin. :(

---

### Post by natpeterson on 2005-08-01
After alien-ing the .rpm and instlaling the .deb, I found the novell client installed in /opt/novell/groupwise/client/ 

I ran /opt/novell/groupwise/client/bin/groupwise and it's working well  :D

---

### Post by muegge on 2005-08-03
I also used alien to get a .deb package, after install it, I started ./groupwise from /opt/novell/groupwise/client/bin, and got the following error message:

Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object

???

---

### Post by iMerlin on 2005-09-14
I tried the Novell forums for this but people keep telling me I'm using 'unsupported' software. If I wanted to play safe... I'd be running Windows 3.11 right now.

[QUOTE=muegge]
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
???[/QUOTE]

This is caused by the JRE installed with the Groupwise Client. I managed to trick the GWclient to use my Java package instead but that only got me one step closer.

 Exception in thread "main" java.lang.UnsatisfiedLinkError: /opt/novell/groupwise/client/lib/libgwapijni.so.1: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.3.4' not found (required by /opt/novell/groupwise/client/lib/libinetpack.so)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(Unknown Source)
	at java.lang.ClassLoader.loadLibrary(Unknown Source)
	at java.lang.Runtime.loadLibrary0(Unknown Source)
	at java.lang.System.loadLibrary(Unknown Source)
	at com.novell.gw.engine.Engine.<clinit>(Unknown Source)
	at com.novell.gw.jclient.bl.eng_impl.EngineCommandManager.<init>(Unknown Source)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
	at java.lang.reflect.Constructor.newInstance(Unknown Source)
	at java.lang.Class.newInstance0(Unknown Source)
	at java.lang.Class.newInstance(Unknown Source)
	at com.novell.gw.jclient.bl.om.GWCommandManager.getInstance(Unknown Source)
	at com.novell.gw.jclient.application.GWClient.getGwCommandManager(Unknown Source)
	at com.novell.gw.jclient.application.GWClient.<init>(Unknown Source)
	at com.novell.gw.jclient.application.GWClient.main(Unknown Source)

---

### Post by muegge on 2005-09-14
I did the alien thing with the gw 6.5 client and everything went fine. Cheers for help an good luck ...

---

### Post by Daimaou on 2006-03-06
I got GroupWise 7 working by doing the following:

[LIST]
[*]Use alien to convert the RPM to a DEB file (alien groupwise-blah-blah-blah.rpm)
[*]Install JAVA (download it from [http://java.sun.com](http://java.sun.com))
[*]Install GroupWise (dpkg -i groupwise-blah-blah-blah.deb)
[*]Delete the /opt/novell/groupwise/client/jre directory
[*]Copy the jre directory from the Java installation you just performed to /opt/novell/groupwise/client/
[*]Run groupwise by typing /opt/novell/groupwise/client/bin/groupwise.sh
[/LIST]

Don't use /opt/novell/groupwise/client/bin/groupwise.  That won't work.  You have to use the groupwise.sh file.

Hope this helps.

---

### Post by glenio on 2006-05-10
I managed to make Novell Groupwise Messenger 1 SP4 work in Slackware 10.2, copying the files from /opt/novell/messenger from a brazilian distro (name's MPUnix, based on Knoppix), and the JRE files from /opt too. It gaves me some headaches to figure out how to do (because here we use SSL to connect, and it gives many errors...).

But on Slackware, Groupwise 6.5 didn't work, shows a weird Java error, and some SSL errors, saying it needs a secure connection...

On Ubuntu (Breezy, and Dapper), I tried the same way that I've done on Slackware, but it didn't work, the same SSL errors.

I tried on SuSE 9.3 too, and Evolution and Gaim to connect. And always the same error: needs a secure connection...

And I didn't find anything on the net to help me out of this...

(sorry for some gramatical errors, I'm not good writing in english. :)

[EDITED]
I've made Groupwise Client work here. Now just the Messenger complains about secure connection...

---

### Post by matthewdhandley on 2007-04-20
> **muegge said:**
> I also used alien to get a .deb package, after install it, I started ./groupwise from /opt/novell/groupwise/client/bin, and got the following error message:

Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object

???

I got that message the first time I installed it. All I had to do was go back and run alien again, but include the scripts modifier:

sudo alien --scripts groupwisefilename.rpm

---

### Post by marcantonio on 2007-05-11
Just wanted to add that if you want the QuickViewer to work you need to install libglib1.2 and libgtk1.2.

Marc

---

### Post by faical117 on 2008-02-20
thanks to Daimaou :guitar:

---

