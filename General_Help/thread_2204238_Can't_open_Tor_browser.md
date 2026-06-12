---
title: "Can't open Tor browser"
date: 2014-02-07
forum: General Help
---

### Post by geovino on 2014-02-07
I'm running Ubuntu 13.10 64 bit with Unity

I've used the Tor browser on many distros but for some reason when I downloaded and extracted it then click on start tor browser icon it brings up a script instead of the browser. 
Its easy in Mint and Debian, but not so in Ubuntu.

How do you open the Tor browser in Ubuntu?

---

### Post by rburkartjo on 2014-02-09
make sure your permission for start-tor-browser is correct.you might have to change it to make sure you can execute it. works great for me. and make sure you click start-tor-browser. good luck

---

### Post by geovino on 2014-02-25
I did that. Why can't I use the Tor browser in Ubuntu? Every other distro does not have this problem. when I click on start tor browser icon I get a bunch of verbiage but not the Firefox tor browser. What is wrong here?

---

### Post by geovino on 2014-02-26
I'm on my main PC running Xubuntu 13.10 and the Tor browser opens with no trouble. Why would Ubuntu be different?

---

### Post by Frogs Hair on 2014-02-26
I have tested the Tor bundle on every version  from 12.04-13'10 successfully. I have to admit I have run Tor very little , but have no trouble starting and using it from the start -tor-browser script. I can only suggest checking that correct version was downloaded  meaning  32 or 64 bit  .

 Tor  installed moments ago on a 12.04 netbook.

---

### Post by geovino on 2014-02-26
> **Frogs Hair said:**
> I have tested the Tor bundle on every version  from 12.04-13'10 successfully. I have to admit I have run Tor very little , but have no trouble starting and using it from the start -tor-browser script. I can only suggest checking that correct version was downloaded  meaning  32 or 64 bit  .

 Tor  installed moments ago on a 12.04 netbook.


Thank you. I will download the browser bundle again and make sure its 64 bit. But I think that's what I downloaded before.

---

### Post by jim_deadlock on 2014-02-27
I'm not able to run it by clicking either, but it works if I launch it from CLI

```
/path/to/start-tor-browser &
```

Or you could create a launcher using that command if you use it frequently.

---

### Post by geovino on 2014-03-01
Still doesn't open:

davek@dave-1310:~$ 
davek@dave-1310:~$ cd Downloads
davek@dave-1310:~/Downloads$ ls
css-layout-2.zip    tor-browser-linux64-3.5.2.1_en-US.tar.xz
Feb 28 tasting.pdf  WT 2014-02-28 - invoice and tasting order.pdf
linowrite.ttf       WT 2014-02-28 - wine info.pdf
tor-browser_en-US
davek@dave-1310:~/Downloads$ cd tor-browser_en-US
davek@dave-1310:~/Downloads/tor-browser_en-US$ ls
Browser  Data  Docs  start-tor-browser  Tor
davek@dave-1310:~/Downloads/tor-browser_en-US$ /start-tor-browser &
[1] 2612
bash: /start-tor-browser: No such file or directory
davek@dave-1310:~/Downloads/tor-browser_en-US$ /start-tor-browser 
bash: /start-tor-browser: No such file or directory
[1]+  Exit 127                /start-tor-browser
davek@dave-1310:~/Downloads/tor-browser_en-US$ 

I'll just use Xubuntu instead

---

### Post by jim_deadlock on 2014-03-01
> **geovino said:**
> $ /start-tor-browser &

The correct command there would be:

```
./start-tor-browser &
```

(note the dot at the front)

The & at the end allows you to close your terminal without killing the Tor browser.

---

### Post by geovino on 2014-03-03
> **jim_deadlock said:**
> The correct command there would be:

```
./start-tor-browser &
```

(note the dot at the front)

The & at the end allows you to close your terminal without killing the Tor browser.

Thanks, that finally got it to open in Tor browser!  But the & didn't keep the browser open. And I can't type in the address box to go to google.com!Too bad you have to do this to get it to work when every other distro all you have to do is click on the short cut! 

Maybe in the 14.04 final things will work as they do in Xubuntu and Mint where I have no trouble using the Tor browser.

---

