---
title: "software center and terminal box"
date: 2016-02-15
forum: General Help
---

### Post by dalu2 on 2016-02-15
i have a Lenovo-3000-G530 running 2 gb ram.  i am running kernal 3.11.0-12-genaric.  i want to upgrade to whatever my computer can handle.  i figured it is a 32 bit cinnamon kernal.  i am a newbie at working within ubuntu although i have been using it for a couple years.  i am interested in upgrading to whatever is free without losing my desktop and/or operating settings.  i dont want to lose my downloaded information.  when i click on the software manager symbol nothing happens.  i gooled how to open or repair/reinstall the center so hopefully it would work.  i opened the terminal box and used a command to reinstall the "software manager".   the command line accepted the search, but asks me for my password.  when i go to type the password nothing happens.  no characters appear. as a result i cannot upgrade at least using that method.  i have been searching for a solution for hours with no luck.  i have never updated/upgraded or even added drivers in linux.  i am looking for a solution that a motivated newbie can use to upgrade my current older version of linux.  i have never worked with a .tarz file.

---

### Post by wyliecoyoteuk on 2016-02-15
"when i go to type the password nothing happens. no characters appear"

That is normal behaviour, the terminal doesn't show your password.

What version of Ubuntu are you using? (the kernel number is not that useful)

[https://help.ubuntu.com/community/CheckingYourUbuntuVersion](https://help.ubuntu.com/community/CheckingYourUbuntuVersion)

---

### Post by dalu2 on 2016-02-18
i agree there is no password, but it doesnt show that ive typed characters either and i tried just typing password that i was prompted to and hitting the enter button a new password prompt line appears.  tried several times.  i wondered if there is some other password besides my login password.

---

### Post by Burgy on 2016-02-18
It will just be the same as your user password (in most cases if your user is an asmin account). Enter the keys and press enter and it will work, you won't see keypresses or symbols for your characters until after successfully or unsuccessfully logging in.
This is normal behaviour as Wylie stated before.

Though your root password can be different from your user password, you were prompted to set a user password when installed your Ubuntu distribution do you remember that step? Is it the same as your current user's?

---

### Post by sultanka on 2016-07-29
> [COLOR=#000000]i agree there is no password, but it doesnt show that ive typed characters either and i tried just typing password that i was prompted to and hitting the enter button to [reset password]("http://www.uukeys.com/reset-windows-8-password-without-disk.html"). tried several times. i wondered if there is some other password besides my login password.[/COLOR]

I have the same problem on 16.04. Tried the above method. and didn't work.

---

### Post by nikefalcon on 2016-07-29
> **sultanka said:**
> I have the same problem on 16.04. Tried the above method. and didn't work.

Like everyone else has said, it is normal behavior for the terminal to  not give any visual feedback when the password is being typed in.
Verify that you are using the correct password with the following command:
```
su $USER 
```
If the password you enter is correct you should not get an authentication failure.

---

