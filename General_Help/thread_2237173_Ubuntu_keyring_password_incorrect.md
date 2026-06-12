---
title: "Ubuntu keyring: password incorrect"
date: 2014-07-31
forum: General Help
---

### Post by Reding on 2014-07-31
Hi everybody. I know there's been plenty of those threads in the past before, reading most of them i still can't find a solution to my problem.

Just after login, or randomly during the use of my computer Ubuntu Gnome Keyring pops up and asks me for a password for my e-mail adress. Iv'e tried all the passwords i could imagine being the correct one, i even changed my login password to match with the keyring one, put myself in auto-login, leaved the field blank. I tried everything ! And still, this damn windows pops up, it's highly annoying.

Please, help me, i'm desperate. It appeared after i installed Mailnag extension with Evolution (which i uninstalled again hoping to solve the keyring problem).

Thanks in advance !

Red

---

### Post by coldcritter64 on 2014-07-31
Try opening dash and type in "Passwords and Keys" and open the keyring with it. This should give access to the stored credentials for the email. You can alter or delete the email details if in there to fix or stop the pop ups.

---

### Post by Reding on 2014-07-31
I've done this before and deleted all of them...

The only one remaining is called " GOA google credentials for identity account_1406743197_0 " (Gnome Online Account)

Thanks for your quick answer

---

### Post by Reding on 2014-07-31
Any ideas guys ?

---

### Post by coldcritter64 on 2014-07-31
This may not necessarily have anything to do with your log in password or keyring password, but with the stored credentials for email. 
Credentials (also containing passwords) are stored in the keyring in entries like the one listed for the Google account.
>  i even changed my login password to match **with the keyring one****1. Did you change your system log in password (also used for sudo access) or did you change an entry like the Google one below to match your log in password ?** This is important to know what you mean exactly here. 

Your keyring password, set the same as your log in password at installation, is stored in a file in your home folder; changing your log in password can put it out of sync with the keyring password on file. 

Entries like the google account containing passwords ARE NOT your "keyring password", just credentials used for other purposes, like automatically logging into an email account with evolution for instance.

> Ubuntu Gnome Keyring pops up and **asks me for a password for my e-mail** adress.

** 2. Is the email address you set up in evolution a gmail (Google) account ? **
Why I ask is because > google credentials for identity account_1406743197_0in the remaining entry.

The password in here is what you use to log into your **email** account. It should NOT be the same as your log in password if that is the case.

Please let me know just how you "changed my login password to match with the keyring one" in the first question. It will be needed to see if you have put the keyring password (on file) out of sync with your log in; this is a separate problem to a wrong password in stored credentials (of which I'm hoping is just the case).

---

### Post by Reding on 2014-07-31
Thanks for your detailed answer to my non-precise description.

[B]> 1. Did you change your system log in password (also used for sudo access) or did you change an entry like the Google one below to match your log in password ?

[/B]Yes, i did change my login password recently AND my e-mail password as well... They are not the same password though.

> **2. Is the email address you set up in evolution a gmail (Google) account ?**

Yes it is.

> Please let me know just how you "changed my login password to match with the keyring one"

I changed it from the "Password and keyring" menu with a right click on one of the left toolbar. I'm not even sure anymore... :(

But they're not matching with each other right now, they're totally different.

Thanks a lot.

Red

---

### Post by mcduck on 2014-07-31
Since you are even able to access and view the keys in the keyring, I'd say the issue has nothing to do with the keyring password (if you didn't have correct keyring, you wouldn'ät be able to unlock it to view the keys).

And actually that's what you even mentioned in the frst post, it's asking for the *e-mail* password.

Anyway, since it's a G-mail account, are you maybe using two-factor authentication for your Google account? That can definitely cause some problems with Gnome's online accounts..

---

### Post by coldcritter64 on 2014-07-31
> **mcduck said:**
> ...Anyway, since it's a G-mail account, **are you maybe using two-factor authentication for your Google account?** That can definitely cause some problems with Gnome's online accounts..

@ OP, this. Thanks mcduck.

---

### Post by Reding on 2014-07-31
Hey.

No, i'm not using two-factor authentication

---

### Post by coldcritter64 on 2014-07-31
I'd suggest you remove the credentials in the keyring for the google account and reset up your google accounts in evolution. As mcduck notes you can see the keyring contents so my previous worry about the passwords being out of sync is moot.

Try logging into your google account by a browser as well to check the credentials directly with the google site first before setting up evolution with the same username / password for the gmail account.

---

### Post by Reding on 2014-07-31
Tried exactly the steps you gave me...
 
The keyring window still pops up and it still shows me that the password i enter is incorrect. It's driving me nuts.

---

### Post by coldcritter64 on 2014-07-31
Can you take a screenshot of the popup and post it as an attachment here please?

Knowing the exact wording will give a better indication of what is happening. I'm not sure if it is now asking for you to unlock the keyring as in your keyring/login password is out of sync or whether it still wants email as with the first popup you noted in the opening post.

When talking about errors it pays to quote exact wording or post a screenshot.

---

### Post by Reding on 2014-08-01
So far so good. After waking up this morning, the keyring problem doesn't show up anymore after login or randomly at times like before neither.

If it stays like this, i'll add a [solved] tag, otherwise i'll be back with a screenshot @coldcritter ;)

---

### Post by Reding on 2014-08-01
It came back :(

[IMG]https://imagizer.imageshack.us/v2/70x70q90/c/674/9eFPwm.jpg[/IMG]

---

### Post by coldcritter64 on 2014-08-01
That picture is so tiny I can't read anything. You need to attach a far larger image so the error can be seen, not just a thumbnail image. 

Or post "word for word" what the error is saying.

---

### Post by Reding on 2014-08-01
Word for word:

> AUTHENTICATION REQUEST

Please enter the password for account *****@gmail.com

Password: ______________________________________

[__]Add this password to your keyring

Cheers mate.

---

### Post by mcduck on 2014-08-01
what applications do you have that might be using gmail? Some e-mail client would come to mind, or maybe you have installed the gmail webapp? Are you actually able to log in to gmail with the password you try use here? And finally, have you marked the checkbox to add the password to the keyring, as otherwise whatever needs it will of course have to ask you every time?

Either way, that's definitely asking for gmail password, and therefore has nothing to do with the keyring password or unlocking it.

---

### Post by Reding on 2014-08-02
Ok, so.

I remember that the problem came up when i installed the "Mailnag extension" by ppa for gnome-shell (which, when you receive an e-mail, opens up evolution). But since i don't use it, i uninstalled the mailnag extension and deleted my infos in Evolution. 

I did marked the checkbox to add the password, and yes, i can login to e-mail account from the browser with that password i'm trying to use for the keyring. The password i type is 100 % correct.

---

### Post by Reding on 2014-08-03
UP ! 

Anybody ?

---

### Post by coldcritter64 on 2014-08-03
> i uninstalled the mailnag extension and deleted my infos in Evolution. You probably should look in your home folder. Show hidden files/folders and look in the .config folder for the evolution folder. Open it and see if any config files for mailnag are left over. Even look for a config folder for the mailnag extension separate to evolution either directly in your home folder or in the .config folder.

This is a bit of a long shot, but it sounds as though your evolution setup is still holding a config for the mailnag extension, hence the continued attempts to authenticate.

Occasionally uninstalling an extension or an application will leave such config files in place, deleting them will then return the application to its original behaviour. If a left over config file is not the problem, I'm pretty much at a loss as I don't use evolution and haven't heard of the mailnag extension until this thread. :) Let us know if you can find anything in your home folder for mailnag. Good luck.

---

### Post by Reding on 2014-08-03
There was nothing in the evolution folder but there was indeed a .mailnag folder in the .config folder.

I deleted it, see what happens eh. 

Will let you know. Thanks.

---

### Post by Reding on 2014-08-04
Still happening...

I'm really losing hope here. It's mental.

---

### Post by cronopiox on 2014-08-22
Hi, 

try this:
[http://superuser.com/questions/741984/evolution-gnome-keyring-wont-remember-google-password](http://superuser.com/questions/741984/evolution-gnome-keyring-wont-remember-google-password)

It worked for me.

J.

---

### Post by OBIEKTYWNY on 2014-09-20
> **cronopiox said:**
> Hi, 

try this:
[http://superuser.com/questions/741984/evolution-gnome-keyring-wont-remember-google-password](http://superuser.com/questions/741984/evolution-gnome-keyring-wont-remember-google-password)

It worked for me.

J.


Thanks a lot cronopiox!
I would confirm that the solution works well on Ubuntu Gnome 14.04. The whole hassle is Google requiring to fill in a CAPTCHA and this is not recognized by Evolution.

---

### Post by logglog on 2014-12-13
It is really simple. I had the same problem.

When you add that gmail account, you will get an email that someone tried to access your email and google blocked it. 
Then you need to go to settings to allow 3rd applications to login  ----> [https://security.google.com/settings/security/activity](https://security.google.com/settings/security/activity)
and just click Allow, thats it..

---

### Post by efajunk on 2015-04-19
Hello!
I solved a problem so [https://www.google.com/settings/security/lesssecureapps](https://www.google.com/settings/security/lesssecureapps)

---

