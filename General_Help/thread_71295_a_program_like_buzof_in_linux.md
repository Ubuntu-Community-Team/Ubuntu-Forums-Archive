---
title: "a program like buzof in linux?"
date: 2005-10-02
forum: General Help
---

### Post by tigen28 on 2005-10-02
Hi,

On windows, I used to use a program called BUZOF
[http://www.basta.com/ProdBuzof.htm](http://www.basta.com/ProdBuzof.htm)

But it's not compatible with linux.  What it does:
1.  goes through opened windows every x seconds
2.  and can close windows of "certain names"

For example, I run auto traffic exchanges with Firefox at night. When some popups, security, or any prompts show up, the program will just close them if I had their names in the program.  A hypothetical situation: I store the name "security error" in the program.  If the window starts with the name "security error," the program will close it.

I think its functions is relatively simple; does anyone knows any application like BUZOF in linux?

Or can anyone tell me what programing I should learn to write such a program? I don't mind of you suggest a print source or html sources.

Any tips or suggestions are greatly appreciated.

Thanks

---

### Post by 23meg on 2005-10-02
devil's pie is a window matching utility that may help you:

[http://www.burtonini.com/blog/computers/devilspie](http://www.burtonini.com/blog/computers/devilspie)

---

### Post by tigen28 on 2005-10-02
Thanks! I'm glimpsing throught it right now.

A very good start, hopefully it'll do all I want it to.

---

### Post by tigen28 on 2005-10-03
Wait, is there a "CLOSE WINDOW" option.  I think I only see 'MAXIMIZE" window, even maximize horizontally and vertically, but no close

any one knows how to "CLOSE" and window in command prompt, or if devilspie has "close" option?

thanks

---

### Post by tigen28 on 2005-10-03
Can't figure out.

How do I install devilspie, or in general, how do I install applications that are not in synaptic?

I figure out how to install packages from synaptic, but that's about all.

please help, thanks

---

### Post by alci on 2005-10-03
Hi,

to install a program not available in synaptic, you usually have to do the following :

1) download the sources files (here devilspie-0.13.tar.gz.tar)
2) extract it in a folder (using file-roller)
3) in the shell (Terminal), go to the directory created by the extraction, and type :

./configure
make install

This should do the trick.

That said, have you added universe to your synaptic's repositories ? Because I  can see devilspie in synaptic, at least here under breezy.

Hope this helps,

Franck

---

### Post by tigen28 on 2005-10-03
Wow, thanks a lot.

that definitely help, I think I will be able to install programs from now on.

as for universe, i don't think it's part of the "auto-update" in hoary, and of couse I don't have it because I didn't know how to install programs manually

I'm gonna try to install my 1st program manually now; I'll post back.

alci and 23meg, thanks again

---

### Post by tigen28 on 2005-10-03
I tried to install devilspie, but when I run the command: "./configure"

configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

any idea where I may download the realated file?

By the way, I install from netbook, maybe I didn't get all the basic file? ...because a c compiler sounds basic

---

### Post by tigen28 on 2005-10-03
nevermind, i'm download some c programming stuff from sysnaptic

still have 1 question though...

Anyone knows how to manually edit devilspie to add a "close option"?

or know how to close a window in the "command prompt"?

thanks

---

### Post by 23meg on 2005-10-04
first of all, devilspie is in the repositories, so you don't have to download and compile it. just type "sudo apt-get devilspie" in the terminal and you'll have installed it. make sure you have the universe repository enabled before you do this.

i'm not sure if devil's pie has a "close window" feature but i'll look into it shortly. after installing it you can type "man devilspie" to read its documentation. i guess there you'll find a list of all accepted parameters that you can configure devil's pie with. as far as i remember, you need to create a file called ".devilspie.xml" in your home folder and put your configuration options there. there will be an example XML config file in your /usr/share/doc/devilspie/examples folder to which you can refer on how to set the parameters.

---

