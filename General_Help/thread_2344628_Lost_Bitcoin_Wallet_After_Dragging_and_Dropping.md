---
title: "Lost Bitcoin Wallet After Dragging and Dropping"
date: 2016-11-26
forum: General Help
---

### Post by gfdgfdgdgfdgdfgd on 2016-11-26
I have over 700 dollars worth of bitcoin in this wallet please help me find them.

I moved my bitcoin wallet from my home folder onto the desktop and it did not show up on the desktop, at the time I was unaware that moving files and folders using the drag and drop method can cause them to be moved to places that you did not intend to move them to. This is ubuntu 12.04 installed alongside windows with WUBI, I tried a foresenics recovery but had no success. I need to find out where it was moved to, I tried commands such as 

ls -l ~/Desktop

history

find . -name .electrum

I was still unable to find it.

Are there logs which show where all files and folders were moved to?

---

### Post by fenrice on 2016-11-27
Don't bitcoin softwares download a huge blockchain file? Maybe you could do something like 

```
[FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif][COLOR=#111111]find / -size +100M[/COLOR][/FONT]
``` 

to find the location? Just a thought

---

### Post by gfdgfdgdgfdgdfgd on 2016-11-27
That command mostly scanned windows and not ubuntu.

So I tried find / -name .electrum under root and I found /home/desktop/.electrum, now if I navigate to desktop and click show hidden files it does not display the folder. So I tried cd Desktop in terminal and then cd .electrum and received an error message displaying "file or directory not found". Anyone know what to do here?

---

### Post by HermanAB on 2016-11-27
Try this instead:
find / -name *electrum

---

### Post by gfdgfdgdgfdgdfgd on 2016-11-27
I was still unable to find it

---

### Post by dragonfly41 on 2016-11-27
Try this ..

sudo updatedb

and be patient for some time (several minutes) while all your files are indexed.

Then run ..

sudo locate electrum

---

