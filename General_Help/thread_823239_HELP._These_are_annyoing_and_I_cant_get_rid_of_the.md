---
title: "HELP. These are annyoing and I cant get rid of them!"
date: 2008-06-09
forum: General Help
---

### Post by Epidemic_HardyBoy on 2008-06-09
The title says it all

Screenshot:

[http://i306.photobucket.com/albums/nn266/epidemic_gfx/Random%20Shit/Screenshot-3.png](http://i306.photobucket.com/albums/nn266/epidemic_gfx/Random%20Shit/Screenshot-3.png)


They cant be deleted, I pulled them off a CD hoping it would just copy them, but apparently not.

Help please. 

(PS Move this if in wrong section)

IM RUNNING UBUNTU 8.04 Hardy

---

### Post by wannadumpwindows on 2008-06-09
There's always the good ole "rm " command, but I'm not gonna be the one to give it to you. Maybe a mod or someone you can trust can help you out real quick. I don't wanna be the guy running around and throwing those commands out there. Too much evill floating around out there . . . . .

---

### Post by PmDematagoda on 2008-06-09
Post the output of:-
```
ls -l ~/Desktop
```

---

### Post by PmDematagoda on 2008-06-09
> **wannadumpwindows said:**
> There's always the good ole "rm " command, but I'm not gonna be the one to give it to you. Maybe a mod or someone you can trust can help you out real quick. I don't wanna be the guy running around and throwing those commands out there. Too much evill floating around out there . . . . .

There is no problem with you giving an rm command as long as the command is given properly and not in a way that may remove any essential user/system files.

---

### Post by Epidemic_HardyBoy on 2008-06-09
Haha, ok

---

### Post by Epidemic_HardyBoy on 2008-06-09
Can you give one to me then o powerful one?

(Sorry for double post.)

---

### Post by PmDematagoda on 2008-06-09
@Epidemic_HardyBoy:- Do not put such big images in a post, just the link or an attachment would be enough.

---

### Post by Epidemic_HardyBoy on 2008-06-09
Ok sorry, but is there any way to get rid of these and the junk in my trashcan too?

---

### Post by VMC on 2008-06-09
> **Epidemic_HardyBoy said:**
> The title says it all

Screenshot:

[http://i306.photobucket.com/albums/nn266/epidemic_gfx/Random%20Shit/Screenshot-3.png](http://i306.photobucket.com/albums/nn266/epidemic_gfx/Random%20Shit/Screenshot-3.png)


They cant be deleted, I pulled them off a CD hoping it would just copy them, but apparently not.

Help please. 

(PS Move this if in wrong section)

IM RUNNING UBUNTU 8.04 Hardy

From your screenshot it says they CAN be deleted. They just can't be moved to the trash.

---

### Post by Epidemic_HardyBoy on 2008-06-09
but whenever I try, it doesnt let me. Ill post up another link to another screeny.

[http://i306.photobucket.com/albums/nn266/epidemic_gfx/Random%20Shit/Screenshot-4.png](http://i306.photobucket.com/albums/nn266/epidemic_gfx/Random%20Shit/Screenshot-4.png)

This says this for every file in the folder.

---

### Post by HunterThomson on 2008-06-09
I think the files are owned by root. Run these commands in a terminal:

cd Desktop

I don't know your user name... I will prtend it is BOB just replace BOB with your user name>>>

chown BOB:BOB Graphics

chown BOB:BOB WinRar3.71

---

### Post by wannadumpwindows on 2008-06-09
> **VMC said:**
> From your screenshot it says they CAN be deleted. They just can't be moved to the trash.

Yeah, the files are just too big for the trash can. It will still delete them for you, they are just gonna be gone forever. You won't be able to go and get them back if you change your mind. Once you hit the button, they're gonna be gone forever!

---

### Post by VMC on 2008-06-09
Have you tried this
```
rm -rf ~/.local/share/Trash/files/*
```

EDIT: I thought you were having problems with your trash can.
Maybe the problem is they are to big to move to trash can.
In that case I don't know what you want to do. I thought you wanted to delte them.

---

### Post by p_quarles on 2008-06-09
From the looks of the desktop screenshot, the files are "locked," which means in reality that they are not owned by the user logged in. Simple way to get rid of them:
1) Open up a root file manager:
```
gksu nautilus
```
2) Open the "Desktop" directory
3) Right-click and delete the unwanted files.

---

### Post by Epidemic_HardyBoy on 2008-06-09
Oh my god, this sucks. Nothing is working.

Not the Chown or the rm..

Damn.

[http://i306.photobucket.com/albums/nn266/epidemic_gfx/Random%20Shit/Screenshot-5.png](http://i306.photobucket.com/albums/nn266/epidemic_gfx/Random%20Shit/Screenshot-5.png)

OK, THANK YOU!

All is cleared up

Now is [Solved]

---

### Post by Martje_001 on 2008-06-09
> **p_quarles said:**
> 2) Open the "Desktop" directory
Make sure you open the one of yourself (/home/name/Desktop).

---

### Post by PmDematagoda on 2008-06-09
If permissions aren't proper, then try this:-
1) Move to the trash can directory(for safety):-
```
cd ~/.local/share/Trash/files/
```

2) Remove all the files with:-
```
sudo rm *
```

---

### Post by VMC on 2008-06-09
> **Epidemic_HardyBoy said:**
> Oh my god, this sucks. Nothing is working.

Not the Chown or the rm..

Damn.

[http://i306.photobucket.com/albums/nn266/epidemic_gfx/Random%20Shit/Screenshot-5.png](http://i306.photobucket.com/albums/nn266/epidemic_gfx/Random%20Shit/Screenshot-5.png)

and how do I open up a root file manager?

sorry im so newbish

Sometimes it takes a drastic measure. I'm sure though that changing the owner or sudo'ing or gk'ing will delete the files.

Can you just change one file to your user and show the listing (ls) of that file and then make sure there's no error when you made the change.
Then try and delete that one file.

I can show the drastic measure later.

---

### Post by p_quarles on 2008-06-09
> **Martje_001 said:**
> Make sure you open the one of yourself (/home/name/Desktop).
True, but the very existence of ~/Desktop folder for the root user is a sign of much deeper problems, so that shouldn't be a problem. If I remember correctly, though, gksu will preserve the current user's location and other environment variables, even while granting root privileges.

---

### Post by Epidemic_HardyBoy on 2008-06-09
Ok, I got the desktop files gone, but the Trash files are still sitting there mocking me..

---

### Post by PmDematagoda on 2008-06-09
> **Epidemic_HardyBoy said:**
> Ok, I got the desktop files gone, but the Trash files are still sitting there mocking me..

Do the commands I've provided in my previous post.

Edit:- Whoops, I just remembered, if those files are in directories within the trash can(and they seem to be), then you would need:-
```
sudo rm -r *
```

---

### Post by Epidemic_HardyBoy on 2008-06-09
Dude, you are the god, Thanks man

---

