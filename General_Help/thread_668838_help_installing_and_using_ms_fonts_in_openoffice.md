---
title: "help installing and using ms fonts in openoffice?"
date: 2008-01-15
forum: General Help
---

### Post by A-dogg on 2008-01-15
I'm having major problems getting OpenOffice to recognize fonts I've installed both to /.fonts and /usr/share/fonts/truetype/msttcorefonts folders. It's really important because I need to use Arial Narrow, but I'm totally stumped. I've run "sudo fc-cache -f -v" and rebooted. Openoffice.org forum suggest running the OO printer administration utility, but I can't find it in Gutsy.

Anyone have any suggestions?!?! :confused:

---

### Post by shane2peru on 2008-01-15
What I do is put my fonts in a folder called myfonts in the /usr/shared/fonts/ folder then run the update command that you ran.  The only other thing that I can think is that when you put your fonts in there they are not set up with the right permissions.  That may be a possible problem.  Mine are set to rwx-xr-x  I don't know if that will help you or not.  If you need help setting your permissions correctly let me know.

Shane

---

### Post by A-dogg on 2008-01-15
actually, I DO need help setting my permissions if you're willing! I'm gonna set up a myfonts folder, as well.

Thanks!

EDIT: I set up the myfonts folder and put arialn.ttf in there using the sudo mv command. still doesn't work. my permissions for the font are set to read&write, read-only, read-only.

---

### Post by kostkon on 2008-01-15
> **A-dogg said:**
> I'm having major problems getting OpenOffice to recognize fonts I've installed both to /.fonts and /usr/share/fonts/truetype/msttcorefonts folders. It's really important because I need to use Arial Narrow, but I'm totally stumped. I've run "sudo fc-cache -f -v" and rebooted. Openoffice.org forum suggest running the OO printer administration utility, but I can't find it in Gutsy.

Anyone have any suggestions?!?! :confused:

This is strange because it should have worked even when you had put the font in the *./fonts* folder. Are you sure the font file is OK and that is not corrupted? Also, is there any possibility that it is an *OpenType* font but with a *.ttf* extension? I am saying this because *OpenOffice* cannot use *OpenType* fonts.

---

### Post by A-dogg on 2008-01-15
When i right click on the font and look at the properties, it says it's a truetype font.

Yeah it's really strange and really annoying as it is screwing up the page-lengths of documents because I can't use the intended fonts. Argh!!!

I don't know for sure that it's not corrupted, but I just copied it out of the fonts directory on my windows xp computer, emailed it to myself and put it in my ubuntu fonts directories. and nada...

---

### Post by shane2peru on 2008-01-15
> **A-dogg said:**
> actually, I DO need help setting my permissions if you're willing! I'm gonna set up a myfonts folder, as well.

Thanks!

EDIT: I set up the myfonts folder and put arialn.ttf in there using the sudo mv command. still doesn't work. my permissions for the font are set to read&write, read-only, read-only.

Ok, this should be pretty simple,

In the terminal type:```

cd /usr/share/fonts/

```
That will put you in the right location, now we are going to change the permissions, type in this:```

sudo chmod 755 myfonts
```
That will set the proper permissions for your folder, also your folder should be owned by root, just in case it isn't we will set that now,```
sudo chown root myfonts
```
then:```
sudo chgrp root myfonts
```
Now we will go into that folder with 'cd myfonts' and we can set the permissions for the actual fonts with this:```
sudo chmod 755 *
```
Now you should be able to run:```

fc-cache -v
``` and you should have all your fonts at your disposal.

If you have any questions, or run into any problems let me know and I will see what I can do to help.  The reason I make my own folder is because I really messed up my fonts once messing with the original fonts folder and ended up in a real mess, so it is perhaps advisable to keep your fonts in a separate folder, and not touch the original folders it makes.  Let me know if that works for ya.

Shane

---

### Post by HermanAB on 2008-01-15
You don't need the MS fonts.  That is what the Redhat Freedom Fonts are for.

Cheers,

Herman

---

### Post by kostkon on 2008-01-15
> **A-dogg said:**
> When i right click on the font and look at the properties, it says it's a truetype font.

Yeah it's really strange and really annoying as it is screwing up the page-lengths of documents because I can't use the intended fonts. Argh!!!

I don't know for sure that it's not corrupted, but I just copied it out of the fonts directory on my windows xp computer, emailed it to myself and put it in my ubuntu fonts directories. and nada...

Just two small questions: when you double-click on the font file do you get a preview of the font? If yes, do the letters look OK?

---

### Post by shane2peru on 2008-01-15
You should be fine copying the font file out of windows, however I guess it could be a possibility it is corrupted, however, I had problems setting mine up in the beginning, and had to change the permissions around to get them working correctly.  I just kept tinkering till I got them working.  If they are corrupted, you will need to re-copy them out of Windows.  I do have Arial Narrow in my OpenOffice Font selections.

Shane

---

### Post by A-dogg on 2008-01-15
the fonts look fine when I double-click on them.

no idea what the redhat freedom thing is

shane -- thanks for taking the time to write all that out, but it didn't work. still nothing. should I maybe log out and back in?


perhaps I should just stall office in my virtualbox xp? this is getting ridiculous...

---

### Post by shane2peru on 2008-01-15
> **A-dogg said:**
> the fonts look fine when I double-click on them.

no idea what the redhat freedom thing is

shane -- thanks for taking the time to write all that out, but it didn't work. still nothing. should I maybe log out and back in?


perhaps I should just stall office in my virtualbox xp? this is getting ridiculous...

I'm sorry that didn't work, maybe try rebooting, I'm not sure.  I have tons of fonts to choose from, but it has been a while since I did all that.  Try rebooting, if not, keep searching you will find the answer, or someone will have the answer.

Shane

---

