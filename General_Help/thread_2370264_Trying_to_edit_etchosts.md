---
title: "Trying to edit /etc/hosts"
date: 2017-09-01
forum: General Help
---

### Post by grey1beard on 2017-09-01
My isp has migrated to new servers, and requires me to add a new line to my /etc/hosts file.
The instruction link directed me to a howtogeek.com page where it gives instructions for doing it in Ubuntu (albeit for 10.04, though I am using 14.04 ) using vim.
I've downloaded and installed vim, then following the example, opened terminal and pasted **sudo vim /etc/hosts**, and it gave me the list of hosts.
However, I can't add the new line as required. I can move the cursor, but not type anything.

What am I doing wrong, or not doing right ?

Many thanks for any help,
John

---

### Post by steeldriver on 2017-09-01
vim isn't the most intuitive editor if you're not familiar with it - you need to hit 'i' to get into 'insert mode'

I'd suggest you use nano instead - which should be installed by default

---

### Post by TheFu on 2017-09-01
Well, vim isn't an editor for someone completely new to Linux.  It doesn't work like any other editor made.  You can run **vimtutor** to get the basics that would allow you to get started with vim. Vim has different modes and it starts in a mode that doesn't allow modification of a file.

You will probably be happier using nano.

```
$ sudo nano /etc/hosts
```

I would like to stress that vim in the hands of an expert is unlike any productivity tool made.  **It is awesome.**  But, as with most non-intuitive tools, it requires effort to learn and hone your skills in vim or vi. That can take years, since vim is highly extensible and customable.  Getting to intermediate level takes just a month or so.

 This would be very useful if you ever want to NOT be a point-n-click user.  I've never seen a router that didn't have something like vim and none of them have nano or any other simple editor like it.  In short, learn vim.

I would use nano today, if I were you.

So ... the real, best, way to be editing this file is 
```
export EDITOR=nano
sudoedit /etc/hosts
```

If you place that *export* line in your ~/.bashrc (top or bottom, doesn't matter), then you'll never need run it again and just the **sudoedit** line is needed going forward.  That is how you should edit **any** system file going forward.  Much safer.  If you want to use a different editor, just change the EDITOR environment variable.  

sudoedit solves all sorts of issues editing files.  If you are on a desktop and want to use a GUI editor, perhaps geany or gedit or kedit, then just place those into the EDITOR environment variable.  But those won't work on non-GUI systems.

---

### Post by grey1beard on 2017-09-01
Grateful thanks.
Do I just close the terminal window to save ?

No, I've just found how to, but when I come to rename the file, it adds an alphanumeric extension.
Is that correct, or should I just save the file with its original name?

---

### Post by grey1beard on 2017-09-01
Now getting a bit frustrated at not being able to exit !
Keeping the original file name, yes, then cntrl + x , or cntrl + o, but nothing happens.
Still doing something wrong
 :(

---

### Post by TheFu on 2017-09-01
cntl-x will ask you to confirm the filename to be saved.  <enter> will accept the default.  Depending on whether you use sudo nano or sudoedit will determine what that default name is. sudoedit will save to a temporary file, then - behind the scenes - copy it to the name you specified at the start.  It is a security feature.

All these little things become second nature, the more you learn and experience.  For almost anything, there will be a tutorial video on youtube.  If you get stuck, it might be worth going there?

---

### Post by grey1beard on 2017-09-01
Thanks for your help.
Yes, I'd battled through trying lots of things till I got it myself, and I also am a great believer in head banging, for sometimes the wall falls over :)
John
PS I had posted this, I thought about 5 minutes ago, and marked the thread Solved, but that seems to have disappeared. Weird.

---

