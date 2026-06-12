---
title: "Strange squares in Firefox"
date: 2006-08-07
forum: General Help
---

### Post by Eazy© on 2006-08-07
Hi!
I got a little problmen i Firefox. I get these strange squares:
[IMG]http://web.telia.com/~u00175529/tecken.png[/IMG]

These squares appear on all sites, even on these forums. They seem to appear mostly in that little yellow preview box (when you hold your mouse pointer over a link). I have tried to change from UTF-8 to all other in Firefox settings but I dosent matter what I change to. 

Anyone had this also and got an solution?

---

### Post by fourchannel on 2006-08-07
I get that sometimes, In fact that's been a problem I've noticed for a *while* now. But I don't have a solution and kinda assume it is supposed to take the place of "enter"

---

### Post by yopnono on 2006-08-07
> **Eazy© said:**
> Hi!
I got a little problmen i Firefox. I get these strange squares:

These squares appear on all sites, even on these forums. They seem to appear mostly in that little yellow preview box (when you hold your mouse pointer over a link). I have tried to change from UTF-8 to all other in Firefox settings but I dosent matter what I change to. 

Anyone had this also and got an solution?

Yes I know, this did not happen in older version of FX like 1.5. I think you need to file a bug at mozilla about this issue.

Since this also happens in the official FX aswell.

---

### Post by tommcd on 2006-08-07
Ummm, "little yellow preview box (when you hold your mouse pointer over a link)".
I don't even get that! Or those strange squares. Is this an extension or something?

---

### Post by yopnono on 2006-08-07
> **tommcd said:**
> Ummm, "little yellow preview box (when you hold your mouse pointer over a link)".
I don't even get that! Or those strange squares. Is this an extension or something?

It's most of the time a "<br>" = new line (not a printable character) and they should not be visible. So it's a bug.

---

### Post by tommcd on 2006-08-07
Thanks! 
btw, I have always used just plain vanilla FF browser with no extensions, in both windows and ubuntu, and I have never had a problem with FF. Have you guys tried disabling extensions to see if the problem goes away?

---

### Post by yopnono on 2006-08-07
> **tommcd said:**
> Thanks! 
btw, I have always used just plain vanilla FF browser with no extensions, in both windows and ubuntu, and I have never had a problem with FF. Have you guys tried disabling extensions to see if the problem goes away?

Like you..
See attachments:

---

### Post by Eazy© on 2006-08-07
Should I report this bug here?: [https://launchpad.net/distros/ubuntu/+source/firefox/+filebug](https://launchpad.net/distros/ubuntu/+source/firefox/+filebug)

---

### Post by yopnono on 2006-08-07
> **Eazy© said:**
> Should I report this bug here?: [https://launchpad.net/distros/ubuntu/+source/firefox/+filebug](https://launchpad.net/distros/ubuntu/+source/firefox/+filebug)

Or/and at mozilla bugcenter: [https://bugzilla.mozilla.org/](https://bugzilla.mozilla.org/)

---

### Post by SishGupta on 2006-08-07
I do not think that this is a firefox only problem. I do not use firefox and get these too but I cant remember where. I think that i have gotten them in gedit and perhaps but not as likely opera. 

The problem likely lies in the font you use?

---

### Post by nix4me on 2006-08-07
I have those too, for a long time now.

nix4me

---

### Post by yopnono on 2006-08-08
> **SishGupta said:**
> I do not think that this is a firefox only problem. I do not use firefox and get these too but I cant remember where. I think that i have gotten them in gedit and perhaps but not as likely opera. 

The problem likely lies in the font you use?

I don't think so. I happens in Windos aswell, but not in older ver of FX nor in ver was it 2 or 3. Also the square box have a number 000A (in my screendump)
```
[not a printable character]

U+000A <control>

General Character Properties

Unicode category: Other, Control

Various Useful Representations

UTF-8: 0x0A
UTF-16: 0x000A

C octal escaped UTF-8: \012
XML decimal entity: 


Annotations and Cross References

Alias names:
 • LINE FEED (LF)
 • new line (NL), end of line (EOL)
```

---

