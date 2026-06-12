---
title: "Editing sources.list"
date: 2007-06-24
forum: General Help
---

### Post by JimNSB on 2007-06-24
Hi, 
I'm still learning the basics, and can't seem to figure out why I'm unable to edit my sources.list when I follow the steps outlined in the '*Enabling Multimedia*' sticky posted above: [http://ubuntuforums.org/showthread.php?t=413625](http://ubuntuforums.org/showthread.php?t=413625)

After editing, when I try to save/replace the list I get a *read-only/permissions* error; when I simply proceeded to the next step the Win32 codecs loaded (I'm guessing they were found at another source?) but not libdvdcss2 (*not found, obsoleted* error).  I'm not really worried about the codecs; I can see that learning/understanding the cause of the '*permissions*' error is more important.

TIA

---

### Post by strabes on 2007-06-24
Are you using feisty? Just install ubuntu-restricted-extras: ```
sudo apt-get install ubuntu-restricted-extras
```

Check out these pages: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by raja on 2007-06-24
The source.lst file can only be edited if you have admin rights. So if you did not open the file with sudo or gksudo, you will not be able to save changes to it. I am guessing this is what must have happened.

---

### Post by Drate on 2007-06-24
I'm not sure about that gksudo business... I always use just regular old sudo.  Try that. (sudo gedit /etc/apt/sources.list).

Also if you choose to use vim (as opposed to gedit): typing the letter "i" will allow you add text; "Esc" to get out of 'insert mode'; and "Shift" + ":" THEN "x" THEN "Enter"  will save changes and exit.

---

### Post by Enverex on 2007-06-24
You need to be root or use sudo.

---

### Post by JimNSB on 2007-06-24
> **strabes said:**
> Are you using feisty? Just install ubuntu-restricted-extras: ```
sudo apt-get install ubuntu-restricted-extras
```

Check out these pages: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Did that yesterday (in fact, I was using that exact guide!), so they might already be installed, huh?

Any suggestions on what's preventing me from editing my sources list?

TIA

---

### Post by JimNSB on 2007-06-24
> **Drate said:**
> I'm not sure about that gksudo business... I always use just regular old sudo.  Try that. (sudo gedit /etc/apt/sources.list).

Also if you choose to use vim (as opposed to gedit): typing the letter "i" will allow you add text; "Esc" to get out of 'insert mode'; and "Shift" + ":" THEN "x" THEN "Enter"  will save changes and exit.

I was using gedit; added the lines via copy'n'paste, then closed the file to bring up a 'save' box ...now I'm sensing there's more to it than that?

---

### Post by YoG%*@ on 2007-06-24
> **JimNSB said:**
> I was using gedit; added the lines via copy'n'paste, then closed the file to bring up a 'save' box ...now I'm sensing there's more to it than that?
no, that's fine. did you use sudo like the previous posters suggested? did it work?

---

### Post by JimNSB on 2007-06-24
> **Drate said:**
> I'm not sure about that gksudo business... I always use just regular old sudo.  Try that. (sudo gedit /etc/apt/sources.list).

That did it.   

Thanks

When folks post commands beginning with '$', should I be entering that character as well?

---

### Post by raja on 2007-06-24
> **JimNSB said:**
> 
When folks post commands beginning with '$', should I be entering that character as well?

NO. They must have unintentionally included the prompt.

---

### Post by JimNSB on 2007-06-24
> **raja said:**
> NO. They must have unintentionally included the prompt.

Thanks; I realized that right after I posted.  
What was confusing me was that the command still worked, except without the sudo (explains why I wasn't prompted for the password)

---

