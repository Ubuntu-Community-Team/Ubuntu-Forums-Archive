---
title: "Need to customize login process"
date: 2008-07-07
forum: General Help
---

### Post by Mr.Jkate on 2008-07-07
Hello,I need to customize login process. I need to customize login screen. I need one button there and when use clicks it login process with predefined user should start. 
Can any body help me in finding the source code change /configurations details needed for this ?

---

### Post by sayakb on 2008-07-07
You may create two users, (System->Administration->Users and groups)
Now for one user, enable **Automatic login **and keep it **disabled** for others. Select the **Human List** login screen (or any custom screen which has a user list). Simply click on the User's name for which auto login is enabled and login directly without entering password.

---

### Post by cpcnw on 2008-07-07
Can anyone point me in the direction of info?

Id like a text mode login to 1024x768x256 cli prompt.

Then when I want gui I type startx.

This is mainly so I can actually see the boot process?

Ta like !

---

### Post by Mr.Jkate on 2008-07-09
This is not what I'm looking for. I don't have to just change the theme. I need to customize whole login screen as well.

---

### Post by NikoC on 2008-07-09
Hmmz,

I don't have my ubuntu lappy here at the moment, but go to the folder where your themes are stored and open the one containing the theme you want to modify... I think there should be an .xml file in there (which is actually plain text that you can open with gedit, kwrite or mousepad) that contains the make up of the login screen. e.g. position of the login box, which buttons to use, which background to use, etc.

Cheers.

---

