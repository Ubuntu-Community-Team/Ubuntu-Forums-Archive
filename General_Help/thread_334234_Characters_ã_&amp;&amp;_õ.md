---
title: "Characters: ã &amp;&amp; õ"
date: 2007-01-08
forum: General Help
---

### Post by marianom on 2007-01-08
Hi everyone,
 using a generic pc keyboard with 105 keys (selected distribution: spanish), what key combinations do I need in order to write the following characters: ã and õ?  (As in *não* in portuguese).

Thanks in advance.

---

### Post by jocko on 2007-01-08
Do you have an 'Alt Gr' key? I'm not sure if it's present in anything but scandinavian keyboards, but on my (Swedish) keyboard it's the right "Alt" key. If so, do you also have a key labelled with '~', '^' and '..'?
If that's the case, first press 'Alt Gr' and '~/^/..' at the same time and then press 'a' to get ã or 'o' to get õ.

Hope this helps.

---

### Post by marianom on 2007-01-08
Hi jocko, thanks for your answer.
I have no ~ key directly. I need to press Alt Gr + ñ to get it alone but when I try "Alt Gr"+ñ+a it first print the ~ and then a or æ depending on how quick I do it.
I have â, à, á and others but the  ~ is the only one I'm missing in my keyboard. I figure I can get it with other keys combination as you suggest but I'm having a hard time finding it.

---

### Post by jem7v on 2007-01-08
You could try using a different keyboard layout - i.e., one that includes the ~, but then the rest of the keyboard output might not match up with the letters marked on your keys... and unfortunately, the Keyboard Layout Preview in XOrg 7.1 (which Edgy uses) is broken (grrrrrrrr, glares at XOrg developers because it used to work and now it don't) so you can't even check what the letters are going to be.  Still, it might be worth trying because you might find something similar enough to what you're used to that the change wouldn't be so bad.

That's insane that there's no ~ key on your keyboard!  If you go with the American English layout, the ~ would be shift+the key to the left of the #1.  (I just use the American English layout + the compose key to type in Spanish, because the Spanish layout doesn't have all the letters you need for Spanish. *rolls eyes*)  
Anyway, this link includes all the compose key (Alt Gr, I think) sequences... it might help a bit. Maybe. Possibly. [http://webcvs.freedesktop.org/xorg/xc/nls/Compose/en_US.UTF-8?view=co](http://webcvs.freedesktop.org/xorg/xc/nls/Compose/en_US.UTF-8?view=co)

---

### Post by jocko on 2007-01-08
Check this out:
[http://en.wikipedia.org/wiki/Keyboard_layout](http://en.wikipedia.org/wiki/Keyboard_layout)
It looks to me that if you have a spanish keyboard layout it should be Alt Gr + 4?.

---

### Post by marianom on 2007-01-08
jocko, the problem seems that AltGr+4 does not work as a dead key. it writes ~ as soon as I press it, something that also happens with the ñ and with the ¡/¿ key which also produces ~. Conclusion: it looks that the character I find everywhere is the ~. Too bad for me it's never a dead key!!!

jem7v, thanks for your valuable input. I will check as you suggested to see what I can find.
In defense of my poor keyboard (sort of love hate relationship over here), I must say that my spanish keyboard indeed have all the keys I need to write in castilian. As a matter of fact, the only letter in spanish that needs ~ is the ñ which I have as a dedicated key (a: that's why maybe I don't have the standalone ~ key, b: the guys who designed the keyboard favoured quickness against extensibility: a problem of modern times if I might add). My request for ~ in vocals is for writing in portuguese.

Thanks both of you for your time and advices.

---

### Post by Buck2348 on 2007-01-08
marianom, I think I have found a way to do what you want.  I'm still a bit new to Linux and Ubuntu, so if you think this is more than you want to deal with or think it might mess up your system you can of course ignore it.  I learned the basis of this in [this thread]("http://ubuntuforums.org/showthread.php?t=209115").  I just tried this out and it works on my machine, running Edgy 6.10.  First edit the file /etc/environment and add the following line at the end:  ```
export GTK_IM_MODULE=xim
```Now copy a file to your HOME folder: ```
cp /usr/share/X11/locale/en_US.UTF-8/Compose ~/.XCompose
```This file adds a great many characters that you can type using the compose key, and you can edit it to suit yourself.  To make the ã and õ I suggest you search the file for "latin small letter a with tilde" and in the second line that includes those words change "<asciitilde>" to "<t>".  I chose "t" for "tilde" and because that combination seems not to be assigned to anything else.  Do the same for the letter "o".  It's only a few lines farther down.  Now after you log out and restart xwindows, the key combination <compose key><t> + a ought to give you ã, and same for õ.  (I think you  know that to use the Compose key you hold it down with the first keystroke, t in the example, release both and then press the second key.)

If you don't wish to make this change, which may well alter key combinations you use already, you can change the location of the Compose key (which the .Xcompose file calls Multi_key) in System -> Preferences -> Keyboard -> Layout Options -> Compose key position.  Or you can reverse the whole process by removing the line you added to /etc/environment and deleting the ~.XCompose file.  Again, you have to restart to make the changes effective.

Hope this helps.  Post if you have problems.

Buck

---

### Post by marianom on 2007-01-08
Hey Buck, thanks a lot for your suggestions and your time, I really appreciate it.
I will check tomorrow to see how it goes.

I'll let you guys know.

Regards.

---

### Post by jem7v on 2007-01-08
My issue was that the Spanish keyboard layout I found didn't have é or è or the likes; the ONLY accented character it contained was the ñ!

---

