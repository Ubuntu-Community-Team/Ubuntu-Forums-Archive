---
title: "What The Hell Is Going On With My Systems Monitor?"
date: 2008-02-15
forum: General Help
---

### Post by Mark76 on 2008-02-15
Take a look at some of the figures in the screenshot

---

### Post by oldb0y on 2008-02-15
Have you tried a reboot?

---

### Post by Mark76 on 2008-02-15
Just did, and here's a screenshot of the post reboot system

---

### Post by oldb0y on 2008-02-15
They are all the same... Is your system slow?

---

### Post by Mark76 on 2008-02-15
I don't know. I don't have anything to measure it by.

Wait... What do you mean they're: "All the same"?  Some of them are using over 17 billion gigs! :eek:

---

### Post by smartboyathome on 2008-02-15
How much ram does your system have? Unless it is a supercomputer, I doubt it has enough ram to make this happen. Instead, I am guessing it is probably a bug. Try running it in the terminal and seeing if there are any errors.

---

### Post by julian67 on 2008-02-15
what makes you think there is a problem? Inactive applications and daemons using no resources while inactive looks pretty good to me. edit: whoops didn't see the far edge of the enormous screenshot :-)

I think it's just Gnome....can be pretty heavy on your system ;-) Try fluxbox, you might get it down to under 10 million gigs of RAM to boot up, still better than Vista.

---

### Post by Mark76 on 2008-02-15
Here's the terminal output

>  gnome-system-monitor
I/O warning : failed to load external entity "/usr/share/gnome-about/gnome-version.xml"

** (gnome-system-monitor:6157): WARNING **: SELinux was found but is not enabled.


(gnome-system-monitor:6157): Wnck-WARNING **: Unhandled action type (nil)

(gnome-system-monitor:6157): Wnck-WARNING **: Unhandled action type (nil)

(gnome-system-monitor:6157): Wnck-WARNING **: Unhandled action type (nil)

(gnome-system-monitor:6157): Wnck-WARNING **: Unhandled action type (nil)

---

### Post by Mark76 on 2008-02-15
And, for the record, I'm not using Gnome. See sig for details :p

---

### Post by oldb0y on 2008-02-15
Well I don't know what ROX is, but have you tried to re-install the systems monitor?

---

### Post by cknight on 2008-02-16
Does the ouput of 'top' in the command line give you the same results?

---

### Post by Mark76 on 2008-02-16
Nope. Nothing like as weird.

I'd have pasted the output but it's dynamic.

BTW, I removed gnome system monitor as per the suggestion on the previous page and this message came up

> /var/lib/scrollkeeper/fr/scrollkeeper_cl.xml:792: parser error : Extra content at the end of the document
SH</title>

Here's the output of that document from line 792 onwards. I don't know if the problems are related.

> SH</title>
        </sect>
      <sect categorycode="SystemServicesTelnet">
        <title>Telnet</title>
        </sect>
      <sect categorycode="SystemServicesSyslog">
        <title>Syslog</title>
        </sect>
      <sect categorycode="SystemServicesBIND">
        <title>BIND</title>
        </sect>
      <sect categorycode="SystemServicesPrinting">
        <title>Impression</title>
        </sect>
      <sect categorycode="SystemServicesOther">
        <title>Autres</title>
        </sect>
    </sect>
    <sect categorycode="SystemOther">
      <title>Autres</title>
      </sect>
  </sect>
</ScrollKeeperContentsList>

---

