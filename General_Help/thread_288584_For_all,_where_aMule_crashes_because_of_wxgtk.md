---
title: "For all, where aMule crashes because of wxgtk"
date: 2006-10-30
forum: General Help
---

### Post by theFallen on 2006-10-30
Hi,

I found out, that installing gtk2-engine-cleanice and configuring gtks with switch2, that aMule started to work without chrashing.

Hope it works for you too!

---

### Post by raist78 on 2006-10-30
Can you please explain a little more the procedure? I'm not able to find switch2 ... Since i upgraded to Edgy i've a crash with amule while closing the first search tab (never seen that thing in Dapper)

---

### Post by theFallen on 2006-10-30
Okay sorry,
the packages are called gtk-theme-switch and gtk2-engines-cleanice.
After installing them, there has to be the command switch2 in a terminal.
After selecting cleanice, you can start aMule and it shouldn't crash. At least it is what happend to me :)

---

### Post by raist78 on 2006-10-30
Ok, just tried your procedure. Now i'm gonna leave aMule open to see if it doesn't crash (then i will post again to let you know the results :) ). Thank you.

---

### Post by raist78 on 2006-10-31
Nothing to do ... it seems that aMule keeps crashing while doing a search and closing the tab. But perhaps this procedure can keep aMule a little more stable in other situations ;)

---

### Post by theFallen on 2006-10-31
Did you start aMule once from a terminal? What is the error message. I had something like "zero pix size" mentioned. That is the reason why I thought there has to be something wrong with the gui. First I wanted to load a aMule-Skin, but couldn't find one. So I tried this gtk-trick. At least I had luck :P :D
Is it chrashing when there is only one tab? Did you try it by closing with the Button clear (the last one of start, stop, download, ...)
Otherwise leav the window open :D

---

### Post by spacepluk on 2006-10-31
I had the same problem. My workaround was installing amule-daemon, amule-utils and amule-utils-gui.

This way I can start the core and gui separately, and if the gui crashes downloads don't get interrupted. Btw now I can monitor my downloads from the office via ssh/amulecmd :)

Saludossss

---

### Post by javierfh on 2006-11-19
> **spacepluk said:**
> I had the same problem. My workaround was installing amule-daemon, amule-utils and amule-utils-gui.

This way I can start the core and gui separately, and if the gui crashes downloads don't get interrupted. Btw now I can monitor my downloads from the office via ssh/amulecmd :)

Saludossss

Hello,

how do you launch the amule without the ui? and how you launch the ui later on without, stopping the non ui ..
i type amule in terminal but launchs the gui and if it crash whole thing crashes (and believe me it does it often, 10 minutes is a success for me :D )

Javi

---

### Post by spacepluk on 2006-11-19
Hola Javi :P

Once you have installed the packages needed you can start the core typing "amuled &" in a terminal without the quotes. 

You should have an "amule gui" in your Internet menu but you can type amulegui in a terminal if you don't.

Saludosss

---

### Post by javierfh on 2006-11-20
Hola Spacepluk :) 

im spanish but living in cold finland :) but lets keep in english just in case someone else can benefit from the tips.

So i have the gui thingy but i need to try amuled. I have seen that you can invoke the command line version by calling to amulecmd but i guess you need lots of parameters there, that couldnt figure out.
So if you type amuled & how does it know to what servers needs to connect?or ports? Or do you mean that you select the servers afterwards when opening the gui part? And if so...what if that crashes, you mentioned that the "engine"continues with the download...is that true? 
In my case it was so annoying that maximun i could keep it on was 10 minutes...so no chance to get anything..

Well i appreciate all help you can provide :)

Javi

---

### Post by KIAaze on 2007-11-14
I've been having amule crashes too and found this page.
Thanks for the hint about amuled. :)

Here's how to use it if somebody else has problems:

1)Choose a password.
Hash it using MD5:
```
echo -n password | md5sum | cut -d ' ' -f 1
```

2)Open ~/.aMule/amule.conf
Set the key"AcceptExternalConnections" to 1.
Set the "ECPassword" field to the hash you obtained.

3)Launch the daemon:
```
amuled &
```

4)Run amulegui to do whatever you want like in the normal amule.
If you close it, the daemon will continue to run. :)

---

### Post by zazuge on 2008-02-02
one day amule started crashing because of wgtk 
then amuled started crashing too
now aume works fine
but amuled seem to trying forever to connect but don't succeed

to tell you the truth this amule thingy start to irritate me it spent more time crashing
than running ............ X_x

---

