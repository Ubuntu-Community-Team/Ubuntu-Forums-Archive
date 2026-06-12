---
title: "Shutdown Problem"
date: 2007-10-25
forum: General Help
---

### Post by nightfire8199 on 2007-10-25
This may have a obvious and easy answer, but I am not good with Linux at all and cant seem to find it.

The problem is as follows:

I go to the Shutdown Menu (System->Quit) and while in there it has all the usual options. but there  is no shutdown button! I know it used to be there and for some odd reason it is no longer available, Any ideas?

picture added for reference (in case you look, I am writing this post in the background...lol)

---

### Post by Abandon on 2007-10-25
> **nightfire8199 said:**
> This may have a obvious and easy answer, but I am not good with Linux at all and cant seem to find it.

The problem is as follows:

I go to the Shutdown Menu (System->Quit) and while in there it has all the usual options. but there  is no shutdown button! I know it used to be there and for some odd reason it is no longer available, Any ideas?

picture added for reference (in case you look, I am writing this post in the background...lol)

It happens when you login from a shell with startx. So did you do that?

---

### Post by ddrichardson on 2007-10-25
Is this the first user account?

---

### Post by bleucalme on 2007-10-25
I have the same problem with KUbuntu. I don't have the reboot or the halt button.

I have only one user. It doesn't change anything when modifying options in Kde's "system preferences"

---

### Post by nightfire8199 on 2007-10-25
I have but one user account (unless you count root) and to my knowledge (not sure what it is) I didn't use startx.but if for some reason i had, how would i go about changing it back?

---

### Post by thelocust on 2007-10-25
For all thoughs having this problem are you using your home partition from Feisty? I'm using Kubuntu by the way same problem as bleucalme.

---

### Post by thelocust on 2007-10-25
This was posted on the KDE forums as solved
 
>  
So. As far as I understand, kde cooperates with kdm a lot. I have just setup the kdm and 3 buttons appeared: shutdown, logoff, and change user (I can make a mistake a bit [IMG]http://www.kde-forum.org/images/standard/smilies/smile.gif[/IMG] because I'm using Russian locale) 

 
Doesn't make much since to me, try reinstalling kdm I guess if anybody can make since of this let me know.

---

### Post by thelocust on 2007-10-25
Found this to 
 
> I found the solution. But it looks strange. Setting up kdm made the necessary buttons to appear. 
 
I don't know what they mean by "setting up kdm"?

---

### Post by thelocust on 2007-10-26
Bumpity bumpity bump

---

### Post by thelocust on 2007-10-26
I think the anwer is [here ]("http://docs.kde.org/development/en/kdebase/kdm/configuring-kdm.html#kdmconfig-shutdown")I'll have to wait till I get home to try it out.

---

### Post by ddrichardson on 2007-10-26
Are you using KDM/GDM or starting X directly with Startx?

---

### Post by thelocust on 2007-10-26
I assume I am using KDM it's a fresh Kubuntu Gusty install.

---

### Post by nightfire8199 on 2007-10-26
OK after a bit of tinkering i got the fix.

1) go to System->Administration->Login Window(should be 3rd from top)

2) Click on the "Local" tab

3) Find the "Menu Bar" section (**bold** type) 

4) If "Show Actions Menu" is unchecked, check it (i didn't check the second box)

5)Click on the running guy in the top right corner of the top menu bar

6) Your shutdown button should be back

If the check box was already checked, or for some reason this didn't work, I'm not sure what the problem is.

Here is my new screen shot with the working shutdown buttons.

---

### Post by carlos1992 on 2007-10-26
i had a kind of problem but mine was on 7.04 ubuntu and when i click on the shut down buttom the one in the desktop what it should do is a window that say log off shut off and so... but it automatly log off, fortunatly i upgrade to 7.10 and it dissapair

---

### Post by thelocust on 2007-10-26
Any fix for KDE? what did that accomplish so that I can emulate it in KDE.

---

