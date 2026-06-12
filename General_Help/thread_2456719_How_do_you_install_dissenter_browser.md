---
title: "How do you install dissenter browser"
date: 2021-01-18
forum: General Help
---

### Post by sofasurfer on 2021-01-18
I tried installing after downloading from dissenter website. Compyter just sits there. Is there a secret?

---

### Post by CelticWarrior on 2021-01-18
How are you installing it?

---

### Post by HermanAB on 2021-01-18
When installing unpackaged software, start by reading the README and INSTALL files.

---

### Post by CelticWarrior on 2021-01-18
> **HermanAB said:**
> When installing unpackaged software, start by reading the README and INSTALL files.
Yes, of course.
But this one is already packaged in deb or rpm, hence my question above. One would think that downloading the deb file and installing the usual way would be enough.

---

### Post by mc4man on 2021-01-18
> **sofasurfer said:**
> I tried installing after downloading from dissenter website. Compyter just sits there. Is there a secret?
No secret, very simple. I'm sure you'll eventually figure out. 
If not, well, whatever..

---

### Post by HermanAB on 2021-01-18
So if you installed it from a deb or whatever, just run it in a console and look at the error messages.  There may be a missing library or ten.

---

### Post by sofasurfer on 2021-01-20
> **CelticWarrior said:**
> How are you installing it?

With a .deb file and the ubuntu installer

---

### Post by CelticWarrior on 2021-01-20
> **sofasurfer said:**
> With a .deb file and the ubuntu installer

Right... So what's the problem, exactly?

---

### Post by grahammechanical on 2021-01-20
These are the install instructions from the Dissenter download page

> Optimally, let your browser open the deb file with the software  installer, and click install. Otherwise, download the package file and  install it by running sudo dpkg -i dissenter-browser_1.5.114_amd64.deb

Did you use the command line? Or is it the software installer that does nothing?

Regards

---

### Post by sofasurfer on 2021-01-21
I think my problem is that I have a 32 bit kernel. 
I came across a site that say to run this sudo dpkg --add-architecture amd64 to fix that problem. Can anyone verify this or offer another option?

---

### Post by Dennis N on 2021-01-21
> **sofasurfer said:**
> I think my problem is that I have a 32 bit kernel. 
I came across a site that say to run this sudo dpkg --add-architecture amd64 to fix that problem. Can anyone verify this or offer another option?
Find out with:
```
dmn@Tyana:~$ dpkg --print-architecture
amd64

```
What does it show?

---

### Post by sofasurfer on 2021-01-21
> **Dennis N said:**
> Find out with:
```
dmn@Tyana:~$ dpkg --print-architecture
amd64

```
What does it show?

i386

---

### Post by Dennis N on 2021-01-21
> **sofasurfer said:**
> i386
OK, that proves you have a 32-bit kernel. The bad news is that it can't run 64-bit software, which is what your .deb file installs. The "add-architecture amd64" command won't add any capability. You need to get a 32-bit version of your application, if there is one. Otherwise, you are out of luck.

---

### Post by sofasurfer on 2021-01-22
thanks

---

### Post by CelticWarrior on 2021-01-22
There is no 32-bit version therefore you can't install it.
Do you really have a 32-bit CPU? That will be a huge problem moving forward as support for that architecture is in its way out at fast speed.
If, however, you have a 64-bit CPU but decided to install a 32-bit OS for... reasons, then you know what you have to do.

---

### Post by ActionParsnip on 2021-01-22
What is the output of
```

 cat /proc/cpuinfo | grep name

```
Thanks

---

### Post by sofasurfer on 2021-01-22
> **ActionParsnip said:**
> What is the output of
```

 cat /proc/cpuinfo | grep name

```
Thanks

model name	: Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz
model name	: Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz
model name	: Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz
model name	: Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz

$ cat /proc/cpuinfo shows:

Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz

lspcu shows:

Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit

---

### Post by CelticWarrior on 2021-01-23
It's a 64-bit CPU. Why are you using a 32-bit OS?
Backup personal files, install a support 64-bit Ubuntu release, problem solved.

---

### Post by Frogs Hair on 2021-01-23
Just tested an installation  and you do need a 64 bit operating system.  The browser is a slightly modified version of Brave with Duck Duck set as default search. It even has Brave branding.

---

### Post by sofasurfer on 2021-01-24
Ok, I got it. I have a 64 bit cpu. 

I also understand that I need to learn more about "bits". Operating systems can either be 32 or 64 bit. That is a simple concept. 

But commands that tell your cpu "bit" (is this called the archetecture?) can say either 32 bit or 64 bit in reference to differant aspects of the cpu...at least this is what I seem to be noticing. I think there is a archetecture "bit" and an instruction set "bit". Am I seeing thing correctly so far or am I beyond understanding? Please give me some appropriate terminology to research.

---

### Post by CelticWarrior on 2021-01-25
64.bit CPUs support both 32-bit and 64-bit instructions, hence the ```
[COLOR=#000000][INDENT]CPU op-mode(s): 32-bit, 64-bit[COLOR=#222222]
```
and the reason why you were able to install and use a 32-bit OS in your 64-bit hardware, for no good reason apparently.

32-bit CPUs support 32-bit only.[/COLOR][/INDENT]


[/COLOR]

---

### Post by ActionParsnip on 2021-01-25
Why 32bit OS in the 21st century.....?

---

### Post by CelticWarrior on 2021-01-25
> **ActionParsnip said:**
> Why 32bit OS in the 21st century.....?
Great question.
And this isn't an isolated case either. Recently I've found the same situation here and another two at the Portuguese/Brazilian alternative forum. Why people do this is beyond my understanding.

---

### Post by dragonfly41 on 2021-01-25
> **sofasurfer said:**
> Please give me some appropriate terminology to research.

Does this help in understanding 32/64 bit addressing?

[https://en.wikipedia.org/wiki/64-bit_computing](https://en.wikipedia.org/wiki/64-bit_computing)

---

### Post by sofasurfer on 2021-01-26
Ok, I know you guys don't like my (i686) 32bit processor but I'll ask another question anyway.
Why does a Ubuntu 20.04 (64 bit) live DVD work on my old processor?

---

### Post by CelticWarrior on 2021-01-26
> **sofasurfer said:**
> Ok, I know you guys don't like my (i686) 32bit processor but I'll ask another question anyway.
Why does a Ubuntu 20.04 (64 bit) live DVD work on my old processor?

Now this is getting ridiculous.
Your processor is 64-bit. You installed a 32-bit OS but that doesn't change the CPU in any way. That's why a 64-bit OS works and is the ONLY logical option. It wouldn't if the CPU was 32-bit as those only support 32-bit OSes. This was already explained, more than once, and with several links to more in dept information. Exactly what part are you still not grasping?
And why would we hate a thing anyway?

---

