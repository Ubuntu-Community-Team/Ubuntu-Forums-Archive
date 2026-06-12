---
title: "How do I change the spell check file?"
date: 2005-04-07
forum: General Help
---

### Post by closure on 2005-04-07
Is there a base spell check file for all apps? If so how do i change it from US english to UK english?

---

### Post by jobezone on 2005-04-08
[QUOTE=closure]Is there a base spell check file for all apps? If so how do i change it from US english to UK english?[/QUOTE]
Quick answer: 
For GNOME: In gdm, enter your username, and choose your language.
For KDE: In kdm choose your language, or configure it in the KControl Center.
For OpenOffice: It is configured inside the application.

 This is the result of my findings:). Run **Synaptic Package Manager**(synaptic), so you won't get confused and can follow this:).

The state of spellcheckers is a bit of a mess in unix/linux. To resolve this, Ubuntu has virtual packages called **language-support-xx** , where xx is a country code. language-support-en installs both the british and the american dictionaries for the main spellchecker engines used by applications in linux: **aspell** and **myspell**.

**aspell** is the most used, both by GNOME and KDE, and the specific package **aspell-en** installs both british and US dictionaries. It defaults to the language of your system.
You can either change for each GNOME and KDE app the dictionary you want to use (boring), or change your **locales** preference, in a local or global way.
Local: In gdm, enter your username, and choose your language.
Global: If you want all users in your system to use the same language, thus use the same dictionary, run:
```
sudo dpkg-reconfigure locales
```
**myspell** is the spellchecker which Openoffice.org uses (if not the only one, one of the few application which do) . The english packages are separated into **myspell-en-gb** and **myspell-en-us**. So you can either remove the myspell-en-us package, or configure it inside openoffice.

**ispell**, where **wamerican** and **wbritish** are the respective english dictionary packages, and which is slowly being deprecated to aspell.

If you're using kubuntu (KDE in ubuntu), it uses aspell, and is configured in the KControl Center.

---

### Post by Eproxus on 2005-04-27
Is there a way to change the dictionary used without changing the locale in Gnome? I want english interface but swedish spellchecking (in Gaim for example).

Thanks in advance!

---

### Post by jobezone on 2005-04-27
Gaim doesn't seem to have a preference on choosing the dictionary being used by aspell inside it, although some other applications do, like Abiword. 
You can do this:

Use synaptic and search for aspell. Then, only leave installed the swedish dictionary. This will make it the default, thus the one Gaim will use (and leave your desktop language intact).

But if what you want is to have multiple dictionaries installed and switch to swedish in gaim, which is smart, I don't know how. Try asking the gaim developers, [http://gaim.sf.net](http://gaim.sf.net)

P.S.:if you want to spellcheck a single file choosing a specific dictionary do:
aspell -l <language> -c <file>

---

### Post by jobezone on 2005-04-27
[QUOTE=jobezone]Gaim doesn't seem to have a preference on choosing the dictionary being used by aspell inside it, although some other applications do, like Abiword. 
You can do this:

Use synaptic and search for aspell. Then, only leave installed the swedish dictionary. This will make it the default, thus the one Gaim will use (and leave your desktop language intact).

But if what you want is to have multiple dictionaries installed and switch to swedish in gaim, which is smart, I don't know how. Try asking the gaim developers, [http://gaim.sf.net](http://gaim.sf.net)

P.S.:if you want to spellcheck a single file choosing a specific dictionary do:
aspell -l <language> -c <file>[/QUOTE]
 The aspell-doc package (found in synaptic) contais the full documentation of aspell, and somewhere in there it should explain how to choose the environment default language for spellchecking.

And doing "man aspell" says that configuration for aspell is placed in /etc/aspell.conf , but it doesn't exist. I suggest you to check the aspell-doc files (which will be installed in /usr/share/doc/aspell-doc/ (probably)).

---

### Post by Eproxus on 2005-04-28
[QUOTE=jobezone]The aspell-doc package (found in synaptic) contais the full documentation of aspell, and somewhere in there it should explain how to choose the environment default language for spellchecking.

And doing "man aspell" says that configuration for aspell is placed in /etc/aspell.conf , but it doesn't exist. I suggest you to check the aspell-doc files (which will be installed in /usr/share/doc/aspell-doc/ (probably)).[/QUOTE]
 Thanks for the tip, I'll see what I can do...

---

### Post by graabein on 2005-07-05
[QUOTE=Eproxus]Is there a way to change the dictionary used without changing the locale in Gnome? I want english interface but swedish spellchecking (in Gaim for example).[/QUOTE]

Did you manage to change this? I want the same thing but with norwegian instead of swedish.

---

### Post by Eproxus on 2005-07-05
[QUOTE=graabein]Did you manage to change this? I want the same thing but with norwegian instead of swedish.[/QUOTE]

Yes, I did!

I wrote a shell script which started Gaim for me.

 ```
#!/bin/bash
LANG=sv_EN
gaim
exit 0
```

You should of course change *sv_EN* to something more appropriate (no_EN?).

---

### Post by keanedp on 2007-03-08
Old post but figured some others may have the same problem, I did with gaim.  To change the default lang edit /etc/environment and change LANG to:

LANG="en_GB.UTF-8"     //whatever your language is

This enabled Gaim and AbiWord to use the British dict automatically, american spelling was driving me insane!

Hope this helps

---

### Post by Incompetnce on 2007-03-26
Hi, how do I change my default language to british english?

I'm tired of it underlining "flavour", "dialogue" and "axe"

Step by step idiot proof instructions would be ideal. thanks.

i looked through the posts here and i tried 
```
sudo dpkg-reconfigure locales
```
but that just gave me a list of installed dictionaries and said "ok" and then gave me the prompt again.

What is GDM?

---

### Post by dcstar on 2007-03-26
> **Incompetnce said:**
> Hi, how do I change my default language to british english?
........

Tell us what application you are using.

---

### Post by Incompetnce on 2007-03-27
> **dcstar said:**
> Tell us what application you are using.

i want to change the spell check language for firefox, XChat, GAIM etc...

---

### Post by ernstblaauw on 2007-04-27
> **Eproxus said:**
> Yes, I did!

I wrote a shell script which started Gaim for me.

 ```
#!/bin/bash
LANG=sv_EN
gaim
exit 0
```

You should of course change *sv_EN* to something more appropriate (no_EN?).
I had to use LANG=nl_NL.utf8 (so including the extension)

> **keanedp said:**
> Old post but figured some others may have the same problem, I did with gaim.  To change the default lang edit /etc/environment and change LANG to:

LANG="en_GB.UTF-8"     //whatever your language is

This enabled Gaim and AbiWord to use the British dict automatically, american spelling was driving me insane!

Hope this helps
If I change that variable to nl_NL.utf8, my whole Ubuntu is Dutch - something I don't want. So I have to set it in a shell script for Gaim.

[QUOTE=http://gaim.sf.net]
**How do I change the language for the Highlight Misspelled words option?**
Pidgin currently only supports spell checking in your locale language. This is because gtkspell 2 does not offer a good way for us to know which dictionaries are available or to switch between them. This functionality has long been promised for gtkspell version 3, which has been delayed somewhat indefinitely. See gtkspell.sf.net.
[/quote]
That's why it is a little bit clumsy.

---

### Post by nossid on 2007-07-14
> **Eproxus said:**
> Yes, I did!

I wrote a shell script which started Gaim for me.

 ```
#!/bin/bash
LANG=sv_EN
gaim
exit 0
```

You should of course change *sv_EN* to something more appropriate (no_EN?).

If you always start Pidgin from the Gnome Applications menu then there's an ugly but easy way that doesn't require a separate file. Enter the preferences for Main Menu, open the properties for Pidgin and change the command from pidgin to ```
bash -c 'LANG=sv_EN pidgin'
``` It's pretty much the quoted script in one line. Replace pidgin with gaim if that's what you use.

---

### Post by MrLudvig on 2008-01-15
open a terminal and run

[FONT="Courier New"]echo lang sv > ~/.aspell.conf[/FONT]

or change sv to preffered lang

---

