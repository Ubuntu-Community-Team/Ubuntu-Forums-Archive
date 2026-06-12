---
title: "Evolution to Thunderbird ( Tried googling directions but their all out of date)"
date: 2017-01-02
forum: General Help
---

### Post by cwm.030 on 2017-01-02
When trying to export my emails back to Thunderbird I get to the step where it says go to:
/home/chris/.local/share/evolution/mail/local

But I dont see any files with no extention on them. Because if I read correctly, I am suppose to drag the files with no extention at the end to Thunderbird and then launch thunderbird and all my emails would be there?

But in /home/chris/.local/share/evolution/mail/local folder this is all I see?

[http://imgur.com/a/h4EEF]("https://imgur.com/a/h4EEF") <~~~ Screenshot

Help!
Thanks, Chris

---

### Post by #&amp;thj^% on 2017-01-02
See if this helps: [http://www.ubuntugeek.com/how-to-export-your-mails-from-evolution-to-thunderbird.html](http://www.ubuntugeek.com/how-to-export-your-mails-from-evolution-to-thunderbird.html)

---

### Post by cwm.030 on 2017-01-02
Hi,

In the instructions when it says go to ".[COLOR=#445263][FONT=Arimo]evolution/mail/local""

when I open HOME there is no .evolution folder

[/FONT][/COLOR]http://imgur.com/a/Wxui3

[COLOR=#445263][FONT=Arimo]-- Chris


[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2017-01-02
Yes that is still a bit dated...did you look in /home/chris/.local/share/evolution

---

### Post by #&amp;thj^% on 2017-01-03
I had to think about this for a moment.
You know it has been a while since I did this... but what you are looking for is in "/home/chris/.cache/evolution/mail"
Now in that folder you should see A numbered folder that will look along the lines of this"1483418278.4192.4@me-System-Product-Name" in there you should find all that you are looking for

---

### Post by cwm.030 on 2017-01-03
Well what I wound up doing was

Selecting all the emails 

Going File > Export an MBOX for each folder

then install an extension called ImportExportTools I think is its name in Thunderbird.

then slowly import each individual .mbox folder into thunderbird. 

-- Chris

---

### Post by cwm.030 on 2017-01-03
Thanks you guys!

---

