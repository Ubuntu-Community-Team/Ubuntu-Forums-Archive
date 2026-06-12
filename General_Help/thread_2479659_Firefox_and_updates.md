---
title: "Firefox and updates"
date: 2022-10-02
forum: General Help
---

### Post by bjngchn on 2022-10-02
1. Do we have to install firefox via sudo apt-get install command? 
If we do, our private identity is stored in firefox, and I think  firefox, search engines, 
and ubuntu shares revenue from searches. I don't care about revenue, 
but our identity is tracked, or can be tracked when we install via sudo command. 
Is there another way in general, and what are advantages and disadvantages of each.
 I mean, download, install. Does it ever work?   

2. I choose "erase everything"on firefox. But then that firefox window freezes permanently.  

3. Firefox sometimes refuses to open a new page/tab, and insist that I restart. 
What the hell do they plan to do during restrart. If there is an update, 
I will close the window anyway soon, and start it again later anyway.
So,  I think there is something strange/suspicious there. 
They want to do something live,  while it won't be possible to track what exactly they are doing,
 in the name of update.  

4. Can't I update firefox and all others via sudo apt-get update? 
Also when I do this, one of two things happen: error, or a very short update.  

5. Maybe the most important: I open a site on firefox, even before it loads partially, i
t freezes my computer permanently, and I have to push on-off button hard to  kill everything by forece, 
shut down the computer. How can firefox or ubuntu allow this to happen. 
Leave enough room for me to kill processes. Also how do I kill any process.   Use ps and then kill command? 
Anyway, I can't use anything, except, if I'm lucky, move cursor a little bit when whole computer feezes because of
one visited site. So using terminal would be already impossible. 
Why doesn't ctrl-alt-del or alt-f4 work? What are they suposed to do if they won't work.
  
I need some general info here. Not a specific cure. I mean, things should be reasonable, but not always they really are.
Don't try to give a complete answer. Any partial answer is valuable. Not everyone would be comfortable
answering every type of question because of, not being an expert, conflict of interest, and many other reasons.

---

### Post by grahammechanical on 2022-10-02
What version of Ubuntu are you using? The version does make a difference. 

Ubuntu 20.04 installs a version of Firefox that has been packaged using the Debian package management method. It will have a file suffix of .deb. Ubuntu 22.04 installs a version of Firefox that is packaged as a Snap package.

The deb packaged version of Firefox is updated/upgraded by the apt update and apt upgrade commands. It is code audited by Ubuntu developers before it is put into the Ubuntu repositories. The snap packaged version of Ubuntu is maintained by the Firefox developers and updates/upgrades are pushed out by the Firefox developers separately from the Ubuntu developers.

On my install of Ubuntu 20.04 I have location services turned off in System Settings>Privacy. There is a Privacy and Security tab in Firefox settings. It gives us control of what web sites can do when we visit them. 

You might benefit from reading the Ubuntu Data Privacy policy.

> At Canonical, we consider your privacy to be extremely important to  us. These are the fundamental principles that we follow in relation to  your personal information:
      
[LIST]
[*]We don’t ask you for personal information unless we truly need it. 
[*]We don’t share your personal  information with anyone except to provide you with services, products,  to comply with the law, or to protect our rights. 
[*]We don’t store personal  information unless required for the on-going operation of services to  you, to provide you with products, to comply with law or to protect our  rights. 
[*]We will use personal information that you provide to us in accordance with this privacy policy. 
[/LIST]
       Canonical Group Limited (**“we”**, **“us”** and **“our”**)  are committed to protecting and respecting your privacy. Information  collected for or on behalf of the Canonical group of companies will be  the responsibility of Canonical Group Limited.


[https://ubuntu.com/legal/data-privacy](https://ubuntu.com/legal/data-privacy)

Regards

---

### Post by ajgreeny on 2022-10-02
It would be helpful to know which version of Ubuntu you are using and something about your hardware so show us the output of command ***inxi -Fzx***
Please use **Code-Tags** for that terminal output as it makes output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. 
See my signature below for a **How-to**

1
If you are running 22.04 firefox will be installed as a snap package not as the .deb package, so ***apt update*** will not carry out any updates for firefox. This is true of all snap packages.

2
I can not comment about that as I've never done it.

3
The request to restart may simply be that your snap version has updated in the background, something that is not normally controllable by the user unless things have changed.
I do not use any snap packages so can not tell you more detail of their use.

4
See #1 above.

5
Not a problem I see but I do have a keyboard shortcut for ***xkill*** though I suspect that will be useless in a wayland system.
I hit my shortcut and the cursor becomes an X and a click on any window is then immediately killed and closed.

---

### Post by bjngchn on 2022-10-02
Thanks for answers.. Number 5 remains the most important and most open one.  Basically I'm wondering how can a web site  freeze a computer completely just because it was visited a second ago. This shouldn't be possible in today's high tech world.  Or, we should be able to disable part of javascript which allows such easy attacks. Or, part of RAM should be made available to the user only, and used for  process killing purposes.

---

### Post by ajgreeny on 2022-10-02
We still have no idea what hardware you are using which could have a big impact on problem #5 that you mention above so please do show us the output of command ***inxi -Fzx*** as I requested in my last post above.
It will probably also be worth adding the ***uBlock Origin ***add-on to firefox if you don't already use it as it can block some advertising activities that slow down the browser.

---

### Post by bjngchn on 2022-10-03
This is the output: Command 'inxi' not found, but can be installed with:  sudo apt install inxi ........ I don't like add-ons or apps, because they do more than what they claim to do.

---

### Post by mIk3_08 on 2022-10-03
I'm on Ubuntu 22.04 LTS and I'm using the tar bz Firefox and downloaded it from Firefox website. And I setup my Firefox browser as my default web browser. So far so good. I haven't encountered any errors or freezes as you mentioned so far. Regards and cheers.

---

### Post by ajgreeny on 2022-10-03
> **mIk3_08 said:**
> I'm on Ubuntu 22.04 LTS and I'm using the tar bz Firefox and downloaded it from Firefox website. And I setup my Firefox browser as my default web browser. So far so good. I haven't encountered any errors or freezes as you mentioned so far. Regards and cheers.
Same here; it's how I've been using Firefox ever since it became a snap and for me, it works brilliantly.

---

### Post by Impavidus on 2022-10-03
> **bjngchn said:**
> 
3. Firefox sometimes refuses to open a new page/tab, and insist that I restart. 
What the hell do they plan to do during restrart. If there is an update, 
I will close the window anyway soon, and start it again later anyway.
So,  I think there is something strange/suspicious there. 
They want to do something live,  while it won't be possible to track what exactly they are doing,
 in the name of update.  


Firefox runs a separate process for each tab. That's for security, to make it really impossible that data leaks from one site to another, other than via mechanisms designed for that (i.e., cookies, which you can limit/disable). When you install an upgrade, the version of Firefox already running and loaded in memory is different from the version stored on your hard disk. To be really sure that the new process created for the new tab doesn't get any data from the old process, it is a fresh copy, loaded from the hard disk. But that's a different version, which may not work together with the version already running. So, when you update Firefox, you cannot open new tabs until you have restarted Firefox.

---

### Post by TheFu on 2022-10-03
> **bjngchn said:**
> Thanks for answers.. Number 5 remains the most important and most open one.  Basically I'm wondering how can a web site  freeze a computer completely just because it was visited a second ago. This shouldn't be possible in today's high tech world.  Or, we should be able to disable part of javascript which allows such easy attacks. Or, part of RAM should be made available to the user only, and used for  process killing purposes.

You are correct, it shouldn't be possible, but there are bugs in all software. Sometimes websites provide crapy javascript and sometimes websites are specifically designed to crash specific systems.  When I was younger, I setup a webpage that was known to cause a blue screen on MS-Windows.  I thought that was funny.  But all programs have bugs and don't do a perfect job accepting input data - html, images, css, and javascript are just data pulled into our browsers to be displayed as best they can figure out.  Sometimes bad data breaks programs.

I don't see that changing in the next 500 yrs while being flexible to allow almost any crap code to be included in webpages.  Heck, image files are just data to be displayed, but if the file isn't consistent or is malicious, it can be a carrier of a nasty payload.

In the cracking world, one of the best ways to take over any computer is to find a memory handling bug, find a way to consistently force it to happen, then provide a specialized payload to make the computer do what the cracker wants.  In the Unix world, every process runs as a specific userid, within a specific address space.  Finding a way to get outside that address space and run stuff as an other user - hopefully "root" - is really what they want.  Over time, that has become both easier and harder, since the security programmers learn every new trick and actively take steps to prevent methods that worked previously.  But crackers are cleaver too.  They don't use 1 method and have tens of thousands of methods that previously worked.  1 tiny mistake and they can get in.  That tiny mistake can be from programmers or users or admins at any level.  We need to be perfect every time, while they only need to find 1 flaw.  The flaw can be from 1 or 5+ people in the layered security setup.  

Crackers are patient.
Security is hard.

---

### Post by mIk3_08 on 2022-10-03
> **TheFu said:**
> We need to be perfect every time, while they only need to find 1 flaw.  The flaw can be from 1 or 5+ people in the layered security setup.  
Crackers are patient. Security is hard. This is true. I believe in this statement that "security is hard" and must have patience too. To be perfect is impossible but if you have patience and of course combined with hard work nothing is impossible. Thanks TheFu. Regards and cheers.

---

### Post by bjngchn on 2022-10-09
Ok , here is an example, I don't want to advertise anything but this site (be careful here) : badmintoon .net , if visited, freezes the computer . I don't see any content there, when JS is off , I see the title in an asian language, and a blank page and no attack;  on the other hand when JS is on, computer is frozen, still can't see anything because this time computer freezes immediately,..I can move the cursor a little bit at the begining,  but can't do anything, and seconds later even can't move the cursor either. SO, WHAT CAN I do to prevent such a freeze event. If I can just close the tab, this may be enough. Maybe there is something under ABOUT:CONFIG which I can modify to prevent such an attack, or at least slow it down.  This is not a problem about this computer only, others had similar problems. It is about firefox, or its connection with the  operating system.... ALSO, sometimes computer slows down,.. I disconnect from internet (cable one, wireless off), still can't unfreeze; OR, can close attacking tab/window, but freezing continues OR, I can close firefox completely, but computer remaisn slow for a while. How can an attack continue when internet is turned off; no new input must be coming. Can I be infected this way, without downloading anything?.. ALSO some sites downloads some stuff without my consent, when visited, without any click. Also, if I see too many items when I do ps ux, does this mean something wrong?

---

