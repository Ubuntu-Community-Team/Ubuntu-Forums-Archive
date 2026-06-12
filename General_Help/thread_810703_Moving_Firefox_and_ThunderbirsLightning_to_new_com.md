---
title: "Moving Firefox and Thunderbirs/Lightning to new computer"
date: 2008-05-28
forum: General Help
---

### Post by sundial on 2008-05-28
I am selling one computer and want to move my Firefox and Thunderbird information to another computer.  The old one has 7.10 the new one 8.04 (Ububtu)  I needs some step by step directions to do this.  Please note, I am not a Linux programmer so please if your offering help, give me all of the directions and any code that I need to use in a terminal window to accomplish my task.
Thanks in advance,
Sundial

---

### Post by wkulecz on 2008-05-28
Install Thunderbird using synaptic.

Then mount your old /home/TbirdUser partition somewhere and copy the the .mozilla-thunderbird folder from the old home to the new.  Then start Thunderbird and you should have all your mail and account settings ready to go.  Turn on "Show Hidden Files" under the View menu in Nautilus.

I did this for my wife's computer this weekend, worked perfectly.

The same for the .mozilla directory might work, but the installer offered to import her old mozilla settings as part of the installations so I let it.

HTH,
--wally.

---

### Post by Zimmer on 2008-05-28
Firefox..
Assuming you want your bookmarks...

Open up your  Home Folder (Places>Home Folder) 

Press <CTRL-H> to view the hidden folders (they are the ones prfixed with a  .  )
find and open the folder  .mozilla  
look for a folder named randomly   xxxxx.default (mine is something like x7ycc34.default)
inside the folder is a file called bookmarks.html
Copy that file to a USB stick or onto a data cd whatever...
When you have installed the new Ubuntu and opened firefox once, close firefox and
find the .mozilla folder on your New machine.
find the random named folder (it will be a different name but  .default)
rename the bookmarks.html file that is already there to bookmarks.bak


 copy the bookmarks.html file from your old computer to the randomly named folder in the New .mozilla folder on your new machine.


Hope that's easy enough..
as for any extensions/plugins you may have had on your old machine, best to download new ones for the New Firefox....

---

### Post by wkulecz on 2008-05-28
> as for any extensions/plugins you may have had on your old machine, best to download new ones for the New Firefox....


Try to find the User Migration import tool the installer used.  Worked fine for my wife's mozilla 7.04 to 8.04 mozilla.  Or start the new mozilla with the old mozilla directory accessable and use the File->Import settings in the new mozilla app.

Moving the T-bird hidden folder got the extensions/plugins and they automatically updated when I started the new T-bird.

--wally.

---

### Post by sundial on 2008-05-28
My thanks to all for the help in this matter.  I will be doing this transfer on the weekend.  This is one of the few times I have understood the directions from all.  Again my thanks to all.

Sundial

---

