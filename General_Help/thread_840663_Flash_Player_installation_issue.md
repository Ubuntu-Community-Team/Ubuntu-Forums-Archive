---
title: "Flash Player installation issue"
date: 2008-06-25
forum: General Help
---

### Post by hokiesparkles on 2008-06-25
I've tried several times to get Flash Player to actually work as a plug-in in Firefox and in my Google Talk gadget. When I fire up Google Talk gadget, I get this message:
'Oops!

The Google Talk Gadget requires Adobe Flash Player version 9 or higher.
You can install the player here.

To complete the installation, quit all running instances of your browser'

I've gone through all the steps in the terminal, this is what it gave me:
'Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/kel/.mozilla

Proceed with the installation? (y/n/q): y

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.'

I still can't access my Google Talk or view videos in Firefox (like YouTube or anything else that uses Flash Player).

Can anyone give me a hand to fix this or have an idea as to why it's not working?

Thanks!

---

### Post by Vivaldi Gloria on 2008-06-25
Start synaptic (in your system menu) and then search & install

```
flashplugin-nonfree
```

Actually, I suggest that you install

```
ubuntu-restricted-extras
```

which inludes flashplugin-nonfree, various codecs, and other goodies.

---

### Post by hokiesparkles on 2008-06-26
Still getting the same error message on my Google Talk and I still can't view videos on the web.

I checked one of the other forum threads and someone suggested using 'sudo apt-get install ubuntu-restricted extras' which I did and this is what I got in my terminal:

'Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted'

Is there something else you suggest trying to use?

---

### Post by Vivaldi Gloria on 2008-06-26
> **hokiesparkles said:**
> Still getting the same error message on my Google Talk and I still can't view videos on the web.

I checked one of the other forum threads and someone suggested using 'sudo apt-get install ubuntu-restricted extras' which I did and this is what I got in my terminal:

'Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted'

Is there something else you suggest trying to use?

Yeah, I forgot to tell you to enable restricted and multiverse repositories. Start synaptic again, find repos in the settings menu then enable restricted and multiverse repositories. Then click refresh button on the left and then install ubuntu-restricted-extras. 

It is

```
ubuntu-restricted-extras
```

btw, not

```
ubuntu-restricted extras
```

as you wrote it.

---

### Post by oldos2er on 2008-06-26
> **hokiesparkles said:**
> Still getting the same error message on my Google Talk and I still can't view videos on the web.

I checked one of the other forum threads and someone suggested using 'sudo apt-get install ubuntu-restricted extras' which I did and this is what I got in my terminal:

'Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted'

Is there something else you suggest trying to use?

 You need to enable the Medibuntu repositories. See [https://help.ubuntu.com/community/Medibuntu?highlight=(medibuntu](https://help.ubuntu.com/community/Medibuntu?highlight=(medibuntu))

 Also the name of the package is ubuntu-restricted-extras

---

### Post by Vivaldi Gloria on 2008-06-26
> **oldos2er said:**
> You need to enable the Medibuntu repositories. 

No, he doesn't need to enable Medibuntu repos. ubuntu-restricted-extras is in multiverse repos. So it's enough to enable that.

---

### Post by Pjotr123 on 2008-06-26
So it is. However, ubuntu-restricted-extras is not enough for 100 % multimedia support. Plus you will want to get rid of openjdk, which is in that meta-package as well.

I therefore suggest that the topic starter applies this simple and complete how-to:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

### Post by ff1111 on 2008-10-12
The flashblock add on for firefox blocks the google talk gadget in ubuntu. 

If you have the flashblock add on installed, add *google.com to your flashblock whitelist, and the google talk gadget will function normally. (To add to your flashblock whitelist, right click on any flashblock placeholder and choose "flashblock options"

---

