---
title: "gedit wont open a text file"
date: 2006-11-01
forum: General Help
---

### Post by closer9 on 2006-11-01
This has happened to a few files of mine. They are just normal text files but when I try and open them in gedit it complains of the character encoding.
```
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.
```
The specific file that prompted this thread was transfered from another ubuntu box via FTP.

I can open the file fine in vi and pico. I've even tried to edit it in pico, save it, and open it in gedit... but get the same error.

The mime type of the file is "application/x-extension-out", and I'm guessing thats the problem. So my question is, how can I change the mime type, or at least tell gedit to just open the darn file?

Thanks for any help...

---

### Post by aysiu on 2006-11-01
Does it open with Nano or Kate?

---

### Post by closer9 on 2006-11-01
> **aysiu said:**
> Does it open with Nano or Kate?
Yes, pico is a simlink to nano, sorry for not specifying. But yes, it opens fine in nano and vi. I dont have kate installed so i cant tell you if it works with it or not.

---

### Post by aysiu on 2006-11-01
Hm.

What about if you rename the extension to .txt?

Also, does it give the same message whether you double-click the file or you open it within Gedit?

---

### Post by closer9 on 2006-11-01
> **aysiu said:**
> Hm.

What about if you rename the extension to .txt?

Also, does it give the same message whether you double-click the file or you open it within Gedit?
The file was extension-less... so I added .txt to the end. The icon changed to a standard text icon, but gedit still gives me that message. I get the same thing if I double click or open gedit and select the file.

I just installed "leafpad" (random text editor i saw in add/remove) and it opens it fine. Bluefish opens it fine also.

EDIT: Here is a screen-shot if interested: [http://www.neg9.com/ubuntu/gedit_problem.png](http://www.neg9.com/ubuntu/gedit_problem.png)

---

### Post by po0f on 2006-11-01
closer9,

When you transferred the file via FTP, it probably defaulted to transferring it as a binary file.  Try to download it again as a text file.

---

### Post by closer9 on 2006-11-01
> **po0f said:**
> closer9,

When you transferred the file via FTP, it probably defaulted to transferring it as a binary file.  Try to download it again as a text file.
I thought that might be the problem, so I transfered it as ASCII. Got the same results.

Im just confused as to how it got the "application/x-extension-out" mime type. Im not sure thats the problem.. but thats not a common type. Google doesn't know much about it.

I'm wondering if its because the file contains raw output from nohup. Regardless, gedit shouldnt be so grouchy about it. :-P

EDIT: by raw output, I mean raw text output from a script. The file is basically a text log file.

---

### Post by fragos on 2006-11-02
Why don't you try editing it with nano and then saving.

---

### Post by closer9 on 2006-11-02
> **fragos said:**
> Why don't you try editing it with nano and then saving.

Already tried that. :-P

> **closer9 said:**
> I can open the file fine in vi and pico. I've even tried to edit it in pico, save it, and open it in gedit... but get the same error.

pico is a symbolic link to nano... nano is pico / pico is nano.
Wikipedia: [http://en.wikipedia.org/wiki/Pico_%28text_editor%29](http://en.wikipedia.org/wiki/Pico_%28text_editor%29)

EDIT: I had a buddy of mine try it in fedora... same problem. So this is a Gnome issue, not a Ubuntu one. I would love to post the file, but its pretty big.

---

### Post by closer9 on 2006-11-02
I posted this problem to the Gnome support forums also. Maybe they can shed some light on this problem.

Link to the Gnome support thread.
[http://gnomesupport.org/forums/viewtopic.php?t=11904](http://gnomesupport.org/forums/viewtopic.php?t=11904)

---

