---
title: "copy to clipboard i3 terminator?"
date: 2018-03-19
forum: General Help
---

### Post by Drenriza on 2018-03-19
I have installed Ubuntu Server edition on my Lenovo L570 laptop with i3 to make a low weight installation.
Now i would like to be able to copy text from my terminal (terminator) window to my clipboard, but this does not work.

I cannot highlight text from the terminal so i also cannot right click and press 'copy' or paste which i also would like to do.
I was looking at some clipboard managers to see if i could figure out how to solve this, where i looked at 'xclip'
but i could not get it to work.

I read here (as an example) [https://superuser.com/questions/436890/cant-copy-to-clipboard-from-vim](https://superuser.com/questions/436890/cant-copy-to-clipboard-from-vim) that vim does not have access to the clipboard without the 'vim-gtk' package.
Is this kind of the same thing for terminator and i3? This is my first time trying to make a light weight install, aka not installing Ubuntu Desktop.

Thanks in advance

---

### Post by #&amp;thj^% on 2018-03-19
Do you have a Menu bar on terminator?
if so see screenshot:
Or just right click in the terminator window and select preferences.
After that is set>>>  "Copy on selection"
Hold the Shift Key hightlight and copy and paste to your clipboard.

---

### Post by oldos2er on 2018-03-19
You do need a clipboard manager of some kind. How exactly does xclip "not work"? Although it's been awhile since I used i3, I believe if you use dmenu to start xclip, it should work. You can also use something like parcellite if you prefer.

---

### Post by Drenriza on 2018-03-19
> You do need a clipboard manager of some kind. How exactly does xclip "not work"
Maybe it did work first time around, after playing with the machine some more i found out that the touchpad had issues with left and right clicking.
So i fixed that, installed xclip, ran it from dmenu and now it works.

That only took more time than i would care to admit :KS

Thanks all for the help and suggestions

---

### Post by #&amp;thj^% on 2018-03-19
Are we still talking about terminator?
EDIT:I don't mean to sound cheeky here but how did you first set-up your i3.conf?
Did you also after creating the default configuration on your first run, it was placed in the &#8220;/etc/&#8221; directory. You have to copy it to your home to customize it.

```
mkdir ~/.i3
sudo cp /etc/i3/config ~/.i3/config
sudo chown user:group ~/.i3/config
```

Don&#8217;t forget to change the ownership of the file to your user. The** user** and **group name **should both match your username.
EDIT I now see you got it sorted...Cheers

---

### Post by oldos2er on 2018-03-19
> **Drenriza said:**
> Maybe it did work first time around, after playing with the machine some more i found out that the touchpad had issues with left and right clicking.
So i fixed that, installed xclip, ran it from dmenu and now it works.

That only took more time than i would care to admit :KS

Thanks all for the help and suggestions

Good news! Would you please mark your thread 'Solved' under Thread Tools at the top of the page? And thank you.

---

