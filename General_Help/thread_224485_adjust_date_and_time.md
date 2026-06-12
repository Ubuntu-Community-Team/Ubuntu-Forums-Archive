---
title: "adjust date and time"
date: 2006-07-28
forum: General Help
---

### Post by hil on 2006-07-28
There might be a bug in Gnome's adjust date and time. Here's how to reproduce it:

1. Right click on the date and time gnome panel widget.
2. Select adjust date & time
3. Check "periodically synchronize clock with Internet servers:"
4. It should prompt that NTP not installed (I forgot the exact phrase)
5. Install NTP in the prompt dialog
6. After installation finishes, come back to the "adjust date & time" dialog
7. Check "periodically synchronize clock with Internet servers:" again

Observed:
   It prompts you to install NTP again. It shouldn't :-x 
Expected:
   Checked without prompting users to install NTP. :KS 

Resolution:
   Close "adjust date & time" dialog and restart it. Repeat step 3. It doesn't prompt you to install NTP :smile:

---

### Post by hil on 2006-07-28
Can someone tell me how to open a bug against ubuntu. Is this a ubuntu or Gnome bug? [https://launchpad.net/distros/ubuntu/+source/gnome-panel/+bug/54379]("https://launchpad.net/distros/ubuntu/+source/gnome-panel/+bug/54379")

---

### Post by noynac on 2006-07-31
I ran into the same problem. Also, I intentionally reset the clock to an incorrect time, and after 24 hours it was never reset to the correct time. I do have all the necessary software installed, and I did select the time servers. 

Noynac

---

