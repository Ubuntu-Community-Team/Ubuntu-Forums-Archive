---
title: "Libreoffice not handling filenames with umlauts"
date: 2024-06-07
forum: General Help
---

### Post by aeh63 on 2024-06-07
Hi
Kubuntu 22.04. Libreoffice won’t open nor save files with names that contain umlauts eg öäå. Saving: ”Error saving the document öä: object not accessible. Thje object cannot be accessed due to insufficient rights”. Opening: ”The operation on öä was started sith an invalid parameter”. Any ideas? Sorry if this is the wrong forum, I couldn’t think of any other.
Rgds
A

---

### Post by QIII on 2024-06-07
Do you have special keyboard shortcuts?

I just saved a file called "Wörterbuch" and was able to open it with Libre Office on Kubuntu.

---

### Post by aeh63 on 2024-06-07
No shortcuts that I know of&#8230;. On my desktop with 22.04 LO handles umlauts perfectly, but my laptop doesn&#8217;t.. I&#8217;ve tried several LO versions, now at 24.xx
Other programs eg Kate handles umlauts.

---

### Post by QIII on 2024-06-07
Interesting.

Letters mit Umlaute are contained in the UTF-8 character encoding standard.  UTF-8 is pretty much a standard across the computing world.

What happens if you use KCharSelect to get, say, ö or ß?  Can you save a file named with one of those copied from a character map?

---

### Post by aeh63 on 2024-06-08
Nope :(

---

### Post by QIII on 2024-06-08
But you can get the letters in the text of the file, correct?

---

### Post by Rubi1200 on 2024-06-08
Have you tried starting in safe mode?

```
libreoffice --safe-mode

```

Try opening or saving with umlauts now; does it make a difference?

And while we are here let's check this:
```
locale

```

---

### Post by aeh63 on 2024-06-09
> **QIII said:**
> But you can get the letters in the text of the file, correct?

Yes

---

### Post by aeh63 on 2024-06-09
[FONT=monospace][COLOR=#000000]$ locale [/COLOR]
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
LANG=en_FI.UTF-8 
LANGUAGE=en_US:en_GB 
LC_CTYPE="en_FI.UTF-8" 
LC_NUMERIC=fi_FI.UTF-8 
LC_TIME=fi_FI.UTF-8 
LC_COLLATE="en_FI.UTF-8" 
LC_MONETARY=fi_FI.UTF-8 
LC_MESSAGES="en_FI.UTF-8" 
LC_PAPER="en_FI.UTF-8" 
LC_NAME="en_FI.UTF-8" 
LC_ADDRESS="en_FI.UTF-8" 
LC_TELEPHONE="en_FI.UTF-8" 
LC_MEASUREMENT=fi_FI.UTF-8 
LC_IDENTIFICATION="en_FI.UTF-8" 
LC_ALL=


[/FONT]

---

### Post by aeh63 on 2024-06-09
[QUOTE=Rubi1200;14193181]Have you tried starting in safe mode?

```
libreoffice --safe-mode

```

Doesn't work...

---

### Post by aeh63 on 2024-06-09
I suspect it's somehow KDE that is the culprit. I just ran Tails on my laptop, started LO and saved a file named xä, it worked. Only thing that doesn't work is LO + KDE...

---

### Post by Rubi1200 on 2024-06-09
I tried replicating this in a VM with Kubuntu 22.04.

Added German as an input method, opened and closed a couple of LO Writer documents with umlauts in the text and filename and they open and save correctly.

Very curious.

What happens if you try this:
Rename the file to remove umlauts >> open or save the file >> rename the file again to include umlauts

It's not much of a workaround but does it solve the issue?

---

### Post by QIII on 2024-06-09
Try issuing the command 

```
touch Lüft
```

in a terminal (while your working directory is your /home) and see if a file is created.

---

### Post by aeh63 on 2024-06-10
I tried touching something with the letter ö, all I got was (arg: 6) ä and å wouldn't work at all, nothing displayed..

---

### Post by Rubi1200 on 2024-06-12
Are you saying that no text document was created in your Home folder?

The touch command creates an empty text file in the current working directory (by default the home folder).

If it did not, then I am beginning to suspect that you need to reconfigure your locale settings.

---

### Post by aeh63 on 2024-06-12
Nothing happened&#8230;
If it is a locale problem, what should I do?

---

### Post by Rubi1200 on 2024-06-13
Do you have the same issue with other foreign accents such as circonflexe or the German sharp S (ß)?

Even though QIII and I are not 100% sure it is a locale issue, try this:
```
sudo dpkg-reconfigure locales
```

Also, I guess it does no harm to check this:

Open LibreOffice and go to Tools -> Options -> Load/Save -> General.

Ensure that "Save" options are configured to use Unicode or UTF-8 encoding.

---

### Post by aeh63 on 2024-06-14
No luck. Besides there is no mention about UTF-8 on the General (as above) settings page&#8230;

---

### Post by Claus7 on 2024-06-14
Hello,

you could check also if something is messed up with your account. One quick test would be to create a new user, log in as that new user and test LO. If it is working with umlauts, then there is something wrong with your account. If not, then the issue is more general. I do not have the UTF-8 on General settings page either. Are you sure that the correct keyboard is selected for your account? One easy thing would be to remove it and add it back again and check.

Some ideas,
Regards!

---

### Post by QIII on 2024-06-14
Do you have Unicode in configs?

Unicode is the character set.  UTF-8 is the encoding.

---

### Post by aeh63 on 2024-06-16
How would I check if I have Unicode in configs?

---

### Post by aeh63 on 2024-06-17
Yes, I created another user, logged in as the new user, saved a document in LO and it worked despite the umlauts! I just don't have any idea how to try to fix this, obviously something broken in my account.

---

### Post by Rubi1200 on 2024-06-17
Try this:

log back in to the main account with the umlaut issues.

Make sure all instances of LO are closed.

Rename the LibreOffice user profile directory
```
mv ~/.config/libreoffice ~/.config/libreoffice-old

```
Restart LibreOffice. A new profile directory will be created automatically.

Try saving/opening with umlauts.

Fixed?

---

### Post by aeh63 on 2024-06-17
Tried it, no luck&#8230;.

---

### Post by Rubi1200 on 2024-06-17
Running out of ideas... :-(

Perhaps check and compare the locale config file on the main user and second user you created to see what, if any, differences there might be.

Can be accessed like this:

```
cat /etc/default/locale
```

---

### Post by aeh63 on 2024-06-21
Solved!!! I changed all regional settings to en us utf 8!!! Thanx 4 the help!

---

### Post by Rubi1200 on 2024-06-21
Excellent!

What a journey that was...

Glad it is finally solved.

---

