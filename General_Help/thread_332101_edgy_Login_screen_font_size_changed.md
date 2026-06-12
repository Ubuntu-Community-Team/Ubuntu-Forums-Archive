---
title: "edgy Login screen font size changed?"
date: 2007-01-05
forum: General Help
---

### Post by allwin on 2007-01-05
I have two old PC's here running UBUNTU.  One I haven't powered up for a week or so.  Today when I powered up, the font in the logon screen, namely the one controling the size of the OPTIONS menu and the user name and password, changed from 10 to what looks like 128 points!  I can only see the top 1/4th of each letter as I type, although if I am careful I can still log on, etc.

Tried to change the themes in GNOME with the system...login window option.  The graphics and color changes but the font size does not.

Where on earth is this font size coded up (that is, in which conf file)?  My next question would be how did it change, but I know that's tough to answer.  I did this even before any automatic updates could be downloaded or sensed, btw.  Basically, I put the horse away a week ago and it was fine, and now it's stumbling after a reboot.

---

### Post by allwin on 2007-01-05
Think I solved it.  From another sort of related thread, I put 
Options "UseEdidDpi" "False"
Options "DPI" "96x96"
into my /etc/X11/xorg.conf file in the screen section.  Now they are OK.  Might have something to do with the nVidia 9631 driver I upgraded to a while back, though I still don't know what changed.

btw, the login font is NOT the same looking as it was.  Used to be in BOLD, now is not bold, so the question remains...where do you set this font for the logon screen, specifically user and password text entry areas?

---

### Post by neoflight on 2007-01-19
the best way to do it is to go to 
```
cd /usr/share/gdm/themes/yourlogintheme
```

and then open the yourlogin.xml
```
sudo gedit yourlogin.xml
```

and identify the login and password fields.... there will be others too such as sessions etc.... change the font size there. REMEMBER to back-up the original file before you edit it....

these settings are OK.
for 1400x1050  ---> font size = 10 - 11
1600 x 1200    -----> 11 - 14

use 
```
ctrl+alt+backspace
``` to restart the x session to see the changes without rebooting...

just play around with different font size and see what fits for you....

hope this helps...

---

### Post by bartman on 2007-01-23
neoflight: Thank you very much! I have had this problem for a while now and while being purely cosmetical it was none the less irritating.

I use the default Human theme and inside */usr/share/gdm/themes/Human/Human.xml* I found this relevant section:
```
              <item type="entry" id="user-pw-entry">
                <normal color="#000000" font="Sans 12"/>
                <pos y="1" x="1" width="-2" height="-2" anchor="nw"/>
              </item>
```The font was absolutely too big so I changed *Sans 12* to *Sans Bold 8* which is perfect! I do have a hi res screen (1920x1200) so know that a bit of experimentation is needed with the font size.

---

### Post by menkent on 2007-05-18
good god. i had to change my user-pw-entry font to size 1 to make it readable.
surely something's not quite right here :???:

---

### Post by lesage on 2007-11-24
Hi,

I'm having the exact same problem, the font In my logon screen is thru the roof  (I'm using ubuntu gutsy gibbon...)

One problem: I can't find the directory in which you say I will solve the problem ..

lesage@hal9000:~$ cd /usr/share/gdm/themes/yourlogintheme
bash: cd: /usr/share/gdm/themes/yourlogintheme: No such file or directory

any Ideas ? 

thanks a lot 

S.

---

### Post by m3alnemer on 2008-03-05
> **lesage said:**
> Hi,

I'm having the exact same problem, the font In my logon screen is thru the roof  (I'm using ubuntu gutsy gibbon...)

One problem: I can't find the directory in which you say I will solve the problem ..

lesage@hal9000:~$ cd /usr/share/gdm/themes/yourlogintheme
bash: cd: /usr/share/gdm/themes/yourlogintheme: No such file or directory

any Ideas ? 

thanks a lot 

S.

try:
```
/usr/share/gdm/themes/Human/Human.xml 
```

---

