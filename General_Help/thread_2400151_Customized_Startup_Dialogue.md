---
title: "Customized Startup Dialogue"
date: 2018-09-03
forum: General Help
---

### Post by webmiester on 2018-09-03
Hi everyone,

When a guest user logs in,   There is a startup dialogue that appears that says:

"All Data Created During this Session will be deleted..."

I like it.  But I want it to display a different message.  How do I make a customized startup dialogue?

Here are some of my ideas, which I hope you can help teach me how to execute them:

Idea 1:  Change the wordings on the startup dialogue of the guest user.
> My problem is I cant find any resource on how to do this.

Idea 2: Remove the startup dialogue and launch a bash script that will write it down on the GUI
> Removing the startup dialogue is easy, I tried the "echo" command in the bash script and it didnt display anything since a terminal wasn't open.  What other commands can I use?  Or perhaps someone can teach me or lead me to a script not necessarily bash that will do this.

Idea 3: Make a graphics file such as .png or .jpg with the message I like then have it displayed on startup
> OK, any ideas how I can do this?  Like is there a command line I can use to display a picture file?


BTW, my system automatically logins to guest user upon boot up.  The strange this is that the wallpaper disappeared when I placed it on autologin.  I find this very wierd, but I dont mind cause its nice without a wallpaper.  It is just that I could have placed the message in the wallpaper instead.

Thanks so much
I hope to hear your suggestions.

---

### Post by jeremy31 on 2018-09-03
Does the /usr/lib/lightdm/guest-session-auto.sh file exist?

---

### Post by webmiester on 2018-09-03
> **jeremy31 said:**
> Does the /usr/lib/lightdm/guest-session-auto.sh file exist?

Yeah, I think it exists.  If it doesnt, I think I can make one.  Can I change the text there?

---

### Post by jeremy31 on 2018-09-03
You should be able to edit it and change line 32

---

### Post by webmiester on 2018-09-03
I accidentally opened the file in the browser, and I found the text there!  Ill try to change the text from the file.  Thanks so much!

---

### Post by webmiester on 2018-09-03
I did something wrong.  Now the dialogue doesnt want to show up anymore.  I didnt make a backup file before altering the file.  Where can I download a default  /usr/lib/lightdm/guest-session-auto.sh?

---

### Post by Holger_Gehrke on 2018-09-04
[https://raw.githubusercontent.com/CanonicalLtd/lightdm/master/debian/guest-session-auto.sh](https://raw.githubusercontent.com/CanonicalLtd/lightdm/master/debian/guest-session-auto.sh)

Holger

---

