---
title: "dconf write word-char-exceptions not taking effect"
date: 2017-01-05
forum: General Help
---

### Post by Salil_Surendran on 2017-01-05
I used this command to set my word char boundaries so that on double-clicking on a sentence in gnome terminal it doesn't just select whole word between whitespace. For eg. in /user/ab/deb when I double click on 'ab' I just want ab to be selected instead of /user/ab/deb which is what is happening now. I followed the post here [http://unix.stackexchange.com/questions/174728/gnome-classic-terminal-mouse-double-click-selection](http://unix.stackexchange.com/questions/174728/gnome-classic-terminal-mouse-double-click-selection)


```
    dconf write /org/gnome/terminal/legacy/profiles:/:b1dcc9dd-5262-4d8d-a863-c897e6d979b9/word-char-exceptions '@ms "-#%&+,./:=?@_~"'

```

I can see the properties on the command line as well as in dconf-editor :


```
    ~>dconf list /org/gnome/terminal/legacy/profiles:/:b1dcc9dd-5262-4d8d-a863-c897e6d979b9/
    default-size-columns
    default-size-rows
    use-theme-transparency
    scroll-on-output
    visible-name
    word-char-exceptions

```

But the value is not taking effect and double clicking is still selecting the whole word between spaces instead of the characters mentioned. I restarted the terminal etc.

---

### Post by mc4man on 2017-01-05
It's not clear what you want, what does white space have to word-char-**exceptions**
The option allows not breaking on the set characters

---

### Post by Salil_Surendran on 2017-01-05
> **mc4man said:**
> It's not clear what you want, what does white space have to word-char-**exceptions**
The option allows not breaking on the set characters  i am trying to follow this particular post as I have the exact same problem [http://unix.stackexchange.com/questions/174728/gnome-classic-terminal-mouse-double-click-selection](http://unix.stackexchange.com/questions/174728/gnome-classic-terminal-mouse-double-click-selection)

---

### Post by mc4man on 2017-01-05
Ok, that works fine here using '@ms "-,.;?%&#_+@~·:$"' to get the results mentioned in the question. 
(- I use slightly different here that also works for what I want ,  '@ms "-,.;:/?%&#_=+@~·"'

What version of libvte & gnome-terminal do you have?
 would show 
```
apt-cache policy libvte-2.91-0 gnome-terminal
```

---

### Post by Salil_Surendran on 2017-01-05
> **mc4man said:**
> 

What version of libvte & gnome-terminal do you have?


Gnome temrinal 3.18.3
Using VTE version 0.42.5 +GNUTLS

---

### Post by mc4man on 2017-01-05
Got me, uses what ever I set here. For example '@ms "null"' makes it only highlight the single word, nothing else.
Are you using the correct, unique to your profile,   id?

---

### Post by xuancong84 on 2017-05-09
I also encounter the same problem. It seems that Ubuntu 16.04 is getting worse. Simply downgrade to Ubuntu 14.04 can solve this problem.

In addition, the default 'less' program that comes with Ubuntu 16.04 is buggy, it does not display line wrapping correctly if a text contains very long UTF-8 lines.

---

