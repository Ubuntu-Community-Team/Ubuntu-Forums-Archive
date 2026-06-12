---
title: "Xine engine needed for Kaffeine"
date: 2006-12-21
forum: General Help
---

### Post by Russty of Oz on 2006-12-21
Hi,

I have a fusion HDTV DVB-T card installed and I tried using Kaffeine to view tv but it said I needed a Xine engine?     So I cheked and I do have Xine installed so I opened it and clicked on the DVB button and got the error in the attachment.

What does this all mean, and is there a fix for it?

Russty

---

### Post by an.echte.trilingue on 2006-12-21
Under kaffeine, what options do you see when you go to settings--> engine ?

If you are using an older Ubuntu, you might need to install a package called kaffeine-xine.

---

### Post by Russty of Oz on 2006-12-21
I am using Edgy, and in the Kaffeine settings it says Kaffeine-Xine.

It still says  "Live digital TV only works with the xine engine"


WAIT!!  

Ahhh!  I just clicked the Kaffeine-Xine line in the settings and now it works.:) 

Thanks for the help.

---

### Post by Russty of Oz on 2006-12-21
Well, almost :-? 

It won't scan any channels?  

Why is nothing simple:(

---

### Post by bh56 on 2007-01-02
I have the same TV card (Dvico-Fusion)
To get kaffeine to work you must have a correct channels file in .kde/share /apps/kaffeine/dvb-t in your home directory. This is a hidden file. To see it select View and Show hidden files in Nautius. You may need root access-I can't remember
In this directory there are a number of Australian examples eg au-Adelaide. Using one of these files as a template change it for your location eg I live in Newcastle. Do a google search to find the frequencies of the transmitters in your area. ABC transmits on 592500000Hz in my area. So I'd change the fourth line of the au-Adelaide file to reflect this. Save the file with a diferent name eg in my case to au-Newcastle.
When you scan for channels select this file from the drop-down list.
If you can, double check the frequencies of the transmitters- the first site I found had incorrect frequencies.
Hope this helps.

---

### Post by pseudonym on 2007-01-02
This process can be made much simpler if you type - ```
sudo apt-get install dvb-utils
``` and then look at the readme in /usr/share/doc/dvb-utils. It shows you how to generate a localised channels.conf file which works with any DVB-capable xine player as well as mplayer. Once it's generated store it in ~/.xine and you should be good to go.

Another good little app is dvbsnoop . It's a command-line utility which can be used to monitor signal strength. Fire it up while you adjust your antenna to get the best reception.

---

### Post by Russty of Oz on 2007-01-02
Thanks guys!

I will give those suggestions a try tomorrow.   At least now I have something to work on.

Russty. :)

---

