---
title: "Install touch friendly apps on desktop"
date: 2015-11-23
forum: General Help
---

### Post by jicha on 2015-11-23
I have a 2in1 notebook with touch display. I would like to install some touch friendly applications on it like picture viewer, browser, file commander etc. How can I install Ubuntu Touch applications on my Kubuntu? Thank you.

---

### Post by Ricardo_Velasco on 2015-12-06
Greeting:

I researched about this and you can install it using an emulator called Ubuntu SDK , I leave some pages instructions to install it :

First installed repositories :

> sudo add-apt-repository ppa:ubuntu-sdk-team/ppa

sudo apt update

sudo apt install ubuntu-sdk

If it's the program then I sent the link so you can run or rather emulate any program Ubuntu Touch

> [http://developer.ubuntu.com/en/apps/sdk/tutorials/running-apps-from-the-sdk/](http://developer.ubuntu.com/en/apps/sdk/tutorials/running-apps-from-the-sdk/)

If I was not objective with your question , sorry because English is not my native tongue

Thank you

---

### Post by Bucky Ball on 2015-12-06
> **Ricardo_Velasco said:**
> 
I researched about this and you can install it using an emulator called Ubuntu SDK , I leave some pages instructions to install it :

First installed repositories

You don't need to drag a PPA in and best not to where you can avoid it. Ubuntu-sdk is in the Ubuntu repositories, Software Centre or Synaptics, and also installable via the terminal.

ALWAYS check there first.

Also, off-topic. The user wants to install some touch friendly apps. That is all. :)

---

### Post by Ricardo_Velasco on 2015-12-06
> **Bucky Ball said:**
> You don't need to drag a PPA in and best not to where you can avoid it. Ubuntu-sdk is in the Ubuntu repositories, Software Centre or Synaptics, and also installable via the terminal.

ALWAYS check there first.

Also, off-topic. The user wants to install some touch friendly apps. That is all. :)


Greeting:

Well I read your comment and thank you too to make me realize you do not need PPA.

But like you said there check and investigate but I think if need PPA.

I put on my terminal if existed in the Ubuntu repositories without adding PPA.

And it came to me:

> ricardo - root @ desktop : / home / ricardo # apt-get install ubuntu-sdk
Reading package lists ... Done
Building dependency tree
Reading state information ... Done
E: It has not been able to locate the package ubuntu- sdk


(My native language is Spanish , the text I translated terminal) 

This certainly does not need PPA ?
I understood that what you publish .

---

### Post by Bucky Ball on 2015-12-06
See the screenshot from my Synaptics attached. No idea why you can't locate it.

I have the Canonical Partners, Independent and Software Restricted by Copyright PPAs enabled in Software and Updates (these are defaults, not added).

Anyhow, as mentioned, this is off-topic so let's hop back on it, please. Feel free to post a thread about ubuntu-sdk if you want to figure out why it's not available for you and we'll dig deeper there. Thanks. :)

---

