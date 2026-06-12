---
title: "Migrating Thunderbird mail folders from windows to ubuntu"
date: 2007-11-08
forum: General Help
---

### Post by enchance on 2007-11-08
How do I copy my Thunderbird emails from Windows to Thunderbird in Ubuntu?

---

### Post by mahousaru on 2007-11-08
You can actually copy the directory across and drop it into where ever your profile is and TB will just use it.  to check your profile information make sure TB is closed. alt F2 and run

thunderbird -profilemanager

Run this command in windows too to find out where the profile is there.

Personally I create a profile where i want it, i dont bother with the email account info as I will over write it.  Close TB, **copy** my original profile into the new directory and when I restart TB everything is nearly the same as it was in windows.  

If you get notification in notification area working can u let me know how :)

---

### Post by michaelzap on 2007-11-08
[QUOTE=mahousaru;3731440]You can actually copy the directory across and drop it into where ever your profile is and TB will just use it./QUOTE]

That's what I was going to say, and if you've ever tried to export mail from Outlook you'll certainly appreciate this!

---

### Post by aysiu on 2007-11-08
Copy from

C:\Documents and Settings\*username*\Application Data\Thunderbird

to 

/home/*username*/.mozilla-thunderbird

You'll have to enable the viewing of hidden folders in both Windows and Ubuntu.

---

### Post by mahousaru on 2007-11-08
> **michaelzap said:**
> [QUOTE=mahousaru;3731440]You can actually copy the directory across and drop it into where ever your profile is and TB will just use it./QUOTE]

That's what I was going to say, and if you've ever tried to export mail from Outlook you'll certainly appreciate this!

Did that once before and I had 5 years of emails.  I nearly had a nervous breakdown doing it.

I just migrated from TB to Evo and it was so easy I was speechless

---

### Post by enchance on 2007-11-08
Let me get this straight, I just copy the contents of

C:\Documents and Settings\username\Application Data\Thunderbird

and paste them (overwrite?) into

/home/username/.mozilla-thunderbird

Is that it?

What if I were using the portable version of Thunderbird from [www.portableapps.com]("http://www.portableapps.com")? Which folder do I have to open here?

---

