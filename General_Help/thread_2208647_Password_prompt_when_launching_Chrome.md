---
title: "Password prompt when launching Chrome"
date: 2014-03-01
forum: General Help
---

### Post by rshaq on 2014-03-01
For the past few versions of Ubuntu, I have considered the Passwords and Keys application, and the annoying password prompts to be my least favorite feature of Ubuntu. I try to keep my installation as stable as possible, so I like removing software via the Software Center. But removal of this application says it wants to also remove ubuntu-desktop, which, obviously I do not want to remove.

I just did a fresh installation of 13.10, and installed Chrome, and logged into Chrome. All of my bookmarks and passwords seem to have been imported. But this stupid Ubuntu password prompt keeps coming up. I typed in a password for it to create a keyring. As soon as I did this, all of a sudden Chrome keeps giving me the old "Your profile could not be opened correctly" message every time I open Chrome.

Is there a way to just remove this stupid keyring application and let Chrome stay signed into my profile? Is it a Google two-factor setting that is messing things up? I've chmodded 777 my entire home directory (I'm the only one using this computer) as one forum suggested, but no good.

Any ideas about how to get Chrome to behave?

---

### Post by Buntu Bunny on 2014-03-01
rshaq, welcome to the Ubuntu Forums. I don't have an answer but I have a similar problem. Any time I go to a website on which I have a password, the password prompt pops up. I don't have a master password set for Chrome so I just click on the X to close the box and carry on as usual. Seems like this started happening right after the last Chrome update.

---

### Post by monkeybrain20122 on 2014-03-01
I never have this problem in Ubuntu. But I have experienced it in Manjaro Linux running xfce. After some big system update Chrome started asking for password everytime it was launched. I don't remember how I fixed it but probably along the line here
             > First make sure libpam-gnome-keyring is installed then log out and back in. 

  When you open Chrome again it will ask for the *password for the keyring* but will give you an option to *unlock the keyring* every time you login. Make sure this is selected and enter your password  to unlock the keyring.
      

[http://askubuntu.com/questions/31786/chrome-asks-for-password-to-unlock-keyring-on-startup](http://askubuntu.com/questions/31786/chrome-asks-for-password-to-unlock-keyring-on-startup)

---

