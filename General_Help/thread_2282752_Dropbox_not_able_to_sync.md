---
title: "Dropbox not able to sync"
date: 2015-06-16
forum: General Help
---

### Post by tiger2000 on 2015-06-16
Hi folks
I think I am experiencing a very weird issue. 
Since few days ago, after some update , my Dropbox application is not able to sync my files. 
The "dropbox icon"just "circle" a lot , without any change . So , I guessed that could be some problem 
to login. I stopped it . 
So , I tried login via browser right to Dropbox website. I tried to login and it did not work. 
I decided try day after, that could be an issue with Dropbox. Tried and did not work again.
I tried using Firefox. Did not work. 
Then, I changed preferences to my Firefox and use the connection via proxy, via the University proxy I study. 
Then, it works. 
Back to Dropbox application. I did the same:set proxy to connection. It works fine. 
So, I have the same situation for the Outlook website (aka Hotmail) , that I am just able to login via Firefox , bypassed by a proxy. 
I had opened another thread in December for this (maybe it's time to see if some good soul provide me an answer for that) . 
It seems that something changed in Ubuntu regarding SSL or something like that. It makes Dropbox not able to login, BUT,the 
weird is : why am I able to login via proxy ? 
Could it be DNS ? 
Any ideas ?
I use UBUNTU 14.04 LTS . From uname -a : Linux XXXXX 3.13.0-46-generic #79-Ubuntu SMP Tue Mar 10 20:06:50 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

thanks in advance

---

### Post by Kurt_Alan on 2015-06-17
I had the same problem, same flavor, after a recent update. I reinstalled via these instructions from dropbox.com tech support:

Run the following commands in your terminal:
&#8194;&#8194;&#8194;&#8194; dropbox stop
&#8194;&#8194;&#8194;&#8194; dropbox status&#8194;&#8194;# Should report "not running"
&#8194;&#8194;&#8194;&#8194; rm -rf ~/.dropbox-dist
&#8194;&#8194;&#8194;&#8194; rm -rf /var/lib/dropbox
&#8194;&#8194;&#8194;&#8194; rm -rf ~/.dropbox*
&#8194;&#8194;&#8194;&#8194; sudo apt-get remove nautilus-dropbox
&#8194;&#8194;&#8194;&#8194; sudo apt-get remove dropbox
&#8194;&#8194;&#8194;&#8194; rm /etc/apt/source.d/dropbox
After this, you can download version 3.4.6 of Dropbox at your command prompt. Depending on your system, you'll need either the 32-bit or 64-bit installer files.
32-bit installer:
cd ~ && wget -O - "https://d1ilhw0800yew8." | tar xzf -
64-bit installer:
cd ~ && wget -O - "https://d1ilhw0800yew8." | tar xzf -
Next, run the Dropbox daemon from the newly created .dropbox-dist folder to install the application:
~/.dropbox-dist/dropboxd

When you use this method you do NOT install nautilus-dropbox via Synaptic: it remains unchecked.
And you start Dropbox from terminal using above command. Just minimize the terminal.

---

### Post by tiger2000 on 2015-06-17
It does not explain "why" I am not  able to login to Dropbox website.

---

