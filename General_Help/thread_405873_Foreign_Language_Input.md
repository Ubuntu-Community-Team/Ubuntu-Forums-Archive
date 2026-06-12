---
title: "Foreign Language Input"
date: 2007-04-10
forum: General Help
---

### Post by quark_77 on 2007-04-10
Hi All,

I am looking for a method to insert foreign characters using the keyboard as I do on microsoft word under windows - I study foreign languages and have to use word to write my essays when I'd much rather use linux. Unfortunately I don't know any easy way to insert characters.

Under word, this is done by holding the control key and pressing ` then e the result being say è if I am working in French, for example.

I'm wondering if there is a simple solution that allows me to do this not only on OpenOffice but throughout linux as well - copy and paste becomes a nuisance when one tries to type quickly. Such a program exists under windows (Accent Composer) but is not free nor is it likely to run under wine.

Does anybody know of such an application? I've looked through synaptic and can't see one, I'm wondering if anyone does what I do and has had a similar experience? My default input method is English UK and I'd like to keep it that way as it's easier to work from my keyboard and produce foreign symbols than apply a french input locale and not know the layout of the keys.

I've also found mention of SCIM and files located in /etc/console-setup/compose-keyboard-locale and I'm not sure if I can use these?

Failing that, I could always do it myself, how would I go about hooking keyboard input for some of my unused keyboard buttons such as the super key or the Fn button? I'm presuming I'd have to write a kernel module to do this and a daemon too.

Thanks in advance for any advice you may have on the matter!!

Quark_77

---

### Post by cisforcojo on 2007-04-10
I'm not sure about accented characters but I have SCIM running really well with typing Chinese characters so that's what I'd recommend.

---

### Post by MichaelT40 on 2007-04-29
Hi there,
I actually had the same question and just figured out how to get accents and things. You just need to go to System>Preferences>Keyboard then select the layout options tab. There is an option for a "compose key" and it seems to be disabled by default. Just set it to a key that seems appropriate (im using my right alt key, though you could use your windows key if you have one). This compose key is a 'dead key' which has no immediate effect when you press it, but alters what comes later.

In short, to get for example the character ü you use the sequence (compose, ", u). That is you press the keys one at a time, not simultaneously. You can also get ß with (compose, s, s). Most of the others are fairly easy to guess.

Hope this helps!

---

### Post by cosmolee on 2007-05-05
I found this Howto helpful:

[http://ubuntuforums.org/showthread.php?t=329656&highlight=accent+characters](http://ubuntuforums.org/showthread.php?t=329656&highlight=accent+characters)

---

### Post by quark_77 on 2007-05-06
Hi All,

Thanks for your help, I am now using the left Windows key for 'Compose' which makes writing French somewhat easier!! Is this just a special feature of gnome or can it be enabled on ttys as well (Ctrl-Alt-F2 for example)?

Quark_77

---

