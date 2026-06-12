---
title: "Trouble with Firefox flash and java"
date: 2007-03-02
forum: General Help
---

### Post by Westerberg on 2007-03-02
When I visit [http://foto.pis.cz/360/prague_360_panoramas/charlesbridge_night1/](http://foto.pis.cz/360/prague_360_panoramas/charlesbridge_night1/) , I get error message stating > This content requires Java Software.

click here to install Java
When I visit [http://tinyurl.com/3azhae](http://tinyurl.com/3azhae) and click on the "zoom" link, I get error message stating 
> An update for the Flash player is required. Click here to get a recent version and then try again

My java version is Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

I'm not sure what version of flash I have, but I *can* view videos on youtube.com.  

Does anyone have some insights/solutions into these problems? 
Thanks

---

### Post by taurus on 2007-03-02
In the address field of firefox, type this command to see which version of flash you have and whether there is a java plugin for it.

```
about:plugins
```

---

### Post by Westerberg on 2007-03-02
Here's the info:
> Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r31

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

> Java(TM) Plug-in 1.5.0_08-b03

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.5.0_08

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;jpi-version=1.5.0_08 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;jpi-version=1.5.0_08 	Java 		Yes


---

### Post by RedSquirrel on 2007-03-03
> **Westerberg said:**
> When I visit [http://foto.pis.cz/360/prague_360_panoramas/charlesbridge_night1/](http://foto.pis.cz/360/prague_360_panoramas/charlesbridge_night1/) , I get error message stating 
When I visit [http://tinyurl.com/3azhae](http://tinyurl.com/3azhae) and click on the "zoom" link, I get error message stating 


My java version is Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

I'm not sure what version of flash I have, but I *can* view videos on youtube.com.  

Does anyone have some insights/solutions into these problems? 
Thanks

I get the same messages you do when I try those sites. Is it possible those sites are misconfigured?

According to 

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

you have the lastest version of Flash.

I have a newer version of Java installed than you do (Java(TM) Plug-in 1.6.0-b105), and I get the same message you do.

---

### Post by osdesk on 2007-04-16
I'm having a similar problem.  Been searching for two days.  I do believe I have installed every possible plugin, extention, etc. to get my flash problem fixed.  I'm running 6.10, Edgy Eft.  I didn't have this problem with previous releases of Ubuntu.  

I can not view any flash at all (youtube, myspace, etc).  I keep getting this message from youtube:

"Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Get the latest Flash player."

Doing about:plugins shows that I have the latest plugins

Anyone else having similar problems or thoughts on a solution? 

Thanks in advance.

---

### Post by joeashcraft on 2007-04-18
javascript works occasionally for me, but I can't reproduce the instance when it does. So I have to use IE4Linux, which is slow, and IE.

---

### Post by RedSquirrel on 2007-04-20
> **joeashcraft said:**
> javascript works occasionally for me, but I can't reproduce the instance when it does. So I have to use IE4Linux, which is slow, and IE.


Do you mean Java?

JavaScript should work all the time as long as you have it enabled. The JavaScript interpreter is part of the browser itself.

---

### Post by sdowney717 on 2007-04-20
Install the extension for firefox called agent switcher. 
Then select netscape or opera and it plays a .mov file in the browser with mplayer plugin.
plays too fast but it is a bunch of pictures of a bridge.

The j.jill site simply works fine for me. NO error message about flash.

I am running feisty.

---

### Post by bwiese on 2007-04-21
> **RedSquirrel said:**
> Do you mean Java?

JavaScript should work all the time as long as you have it enabled. The JavaScript interpreter is part of the browser itself.

To test your javascript, go to this page: [http://segal.org/java/config/index.html](http://segal.org/java/config/index.html)

I'm running Ubuntu 6.10 also, and haven't been able to get "javascript" working!?
I've never encounterend an error like this before.  I removed all extensions, enabled javascript, actually uninstalled firefox (part of ubuntu-desktop) then reinstalled all of that stuff... still, no go.

Any insight into how javascript got broken on 6.10?

Brian

$ dpkg -l firefox
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name            Version         Description
+++-===============-===============-==============================================
ii  firefox         2.0.0.3+0dfsg-0 lightweight web browser based on Mozilla

---

### Post by sdowney717 on 2007-04-21
Is this telling me my javascript is working?

Configuration Test for Java and JavaScript

For your browser we detect:
 
JavaScript is working 

More detailed information about your configuration is sometimes useful:

JavaScript configuration information:

navigator.appName = Netscape
navigator.appVersion = 5.0 (X11; en-US)
navigator.userAgent = Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.3) Gecko/20061201 Firefox/2.0.0.3 (Ubuntu-feisty)
navigator.vendorSub =
navigator.javaEnabled() = true
navigator.platform = Linux i686
navigator.vendor =

Java configuration information:

---

### Post by old_geekster on 2007-04-21
> **bwiese said:**
> To test your javascript, go to this page: [http://segal.org/java/config/index.html](http://segal.org/java/config/index.html)

I'm running Ubuntu 6.10 also, and haven't been able to get "javascript" working!?
I've never encounterend an error like this before.  I removed all extensions, enabled javascript, actually uninstalled firefox (part of ubuntu-desktop) then reinstalled all of that stuff... still, no go.

Any insight into how javascript got broken on 6.10?

Brian

$ dpkg -l firefox
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name            Version         Description
+++-===============-===============-==============================================
ii  firefox         2.0.0.3+0dfsg-0 lightweight web browser based on Mozilla
Good link.  Thanks!

---

### Post by joeashcraft on 2007-04-24
I've got to keep a better watch on my subscribed threads :)


I mean javascript. Java works fine for me (I double check using [this site]("http://www.java.com/en/download/help/testvm.xml")).
According to [http://segal.org/java/config/index.html](http://segal.org/java/config/index.html), "JavaScript is not working."
By 'sometimes' works, I mean that for sites like maps.fon.com, the site is useless to me. But maps.google.com works just fine. Unless they're using different kinds of javascript, I can't think of a reason that javascript works on some sites and not others.

---

### Post by RedSquirrel on 2007-04-25
> **joeashcraft said:**
> I've got to keep a better watch on my subscribed threads :)


I mean javascript. Java works fine for me (I double check using [this site]("http://www.java.com/en/download/help/testvm.xml")).
According to [http://segal.org/java/config/index.html](http://segal.org/java/config/index.html), "JavaScript is not working."
By 'sometimes' works, I mean that for sites like maps.fon.com, the site is useless to me. But maps.google.com works just fine. Unless they're using different kinds of javascript, I can't think of a reason that javascript works on some sites and not others.

That is bizarre. I don't think I've ever heard of that. I know there are differences between the JavaScript implementation on IE and that in Firefox, but it's hard to imagine that a site would use only IE specific stuff. And I tried that maps.fon.com site and it works for me with Firefox... :confused:


I'll let you know if I come across anything...

---

### Post by joeashcraft on 2007-05-06
I finally have JavaScript working (according to [http://segal.org/java/config/index.html)](http://segal.org/java/config/index.html)).
Here's what I did...
backup bookmarks and passwords (I used [FEBE]("https://addons.mozilla.org/en-US/firefox/addon/2109"). [Password Exporter]("https://addons.mozilla.org/en-US/firefox/addon/2848") also works.
I deleted the files in ~/.mozilla/firefox/
I reinstalled firefox via Synaptic

now all i have to do is get my extensions back one by one

---

