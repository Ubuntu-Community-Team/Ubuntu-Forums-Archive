---
title: "Crossover - how do i install it"
date: 2007-02-24
forum: General Help
---

### Post by Tobster on 2007-02-24
:( 

I just purchased and downloaded Cross Over (it an close source version of the Wine software) 
But I have never been able to install a external software on Ubuntu.  

Please could someone help me because this as cost me money and i really need it for college


Thanks

Toby

---

### Post by Tobster on 2007-02-24
Help i really need this  :(

---

### Post by Tobster on 2007-02-24
This is why Linux as failed what the point in an OS  that is so darn had to install software as great as Ubuntu is this is a foundation error

---

### Post by Gerard Barberi on 2007-02-24
There's a file in the folder called "install crossover...".  It's a .sh file.  All you need to do is double click the file.  It should ask you if you want to run, display or run in terminal.  Choose run in terminal.  That should be it.

Oh, the file usually looks like a rolled up scroll.

---

### Post by WiseElben on 2007-02-24
Why don't you check out the manual? [http://www.codeweavers.com/support/docs/crossover-standard/install](http://www.codeweavers.com/support/docs/crossover-standard/install)

Or you can go to the terminal and type:

```
sh name_of_installer.sh
```

---

### Post by Tobster on 2007-02-24
Thanks guys I do it now

---

### Post by Tobster on 2007-02-24
I can not find the 'Run interminal option.

---

### Post by Tobster on 2007-02-24
I have Wine installed I wonder if that is conflicting because i get the following message - see attachment

Thanks

Toby

---

### Post by Tobster on 2007-02-24
help :confused: :(

---

### Post by Gerard Barberi on 2007-02-24
Your screen shot looks like you are trying to use the "package installer".  If you are. you should not be.

From your screen shots it looks like the file is on the Desktop.  Open a terminal and type

cd /home/"your user name"/Desktop

sh install-crossover-standard-6.0.0.sh

EDIT: Wine shouldn't conflict with the above install.

---

### Post by Tobster on 2007-02-24
toby@toby-desktop:~$ 
toby@toby-desktop:~$ cd /home/"your user name"/Desktop
bash: cd: /home/your user name/Desktop: No such file or directory
toby@toby-desktop:~$ cd/home/toby/desktop
bash: cd/home/toby/desktop: No such file or directory
toby@toby-desktop:~$ cd/home/toby/desktop
bash: cd/home/toby/desktop: No such file or directory
toby@toby-desktop:~$ cd/home/toby/Desktop
bash: cd/home/toby/Desktop: No such file or directory
toby@toby-desktop:~$ cd
toby@toby-desktop:~$ sh install-crossover-standard-6.0.0.sh
sh: Can't open install-crossover-standard-6.0.0.sh
toby@toby-desktop:~$

---

### Post by Tobster on 2007-02-24
toby@toby-desktop:~$ '/home/toby/Desktop/install-crossover-standard-6.0.0.sh' 
bash: /home/toby/Desktop/install-crossover-standard-6.0.0.sh: Permission denied
toby@toby-desktop:~$ 

Also failed I feel so stupid

---

### Post by Tobster on 2007-02-24
This is a another screen shot of the failure

---

### Post by Maestro23 on 2007-02-24
Have you did this to the file:

> chmod +x ShellScript.sh
./ShellScript.sh

*ShellScript.sh is where your filename goes.

---

### Post by borris.morris on 2007-02-24
> **Tobster said:**
> toby@toby-desktop:~$ '/home/toby/Desktop/install-crossover-standard-6.0.0.sh' 
bash: /home/toby/Desktop/install-crossover-standard-6.0.0.sh: Permission denied
toby@toby-desktop:~$ 

Also failed I feel so stupid

You should do this, ```
sh /home/toby/Destop/install-crossover-standard-6.0.0.sh
```
If that doesn't work than do ```
chmod a+x /home/toby/Destop/install-crossover-standard-6.0.0.sh
```
and then run the script again.

---

### Post by Tobster on 2007-02-24
toby@toby-desktop:~$ chmod +x ShellScript.sh
chmod: cannot access `ShellScript.sh': No such file or directory
toby@toby-desktop:~$ ./ShellScript.sh
bash: ./ShellScript.sh: No such file or directory
toby@toby-desktop:~$ sh /home/toby/Destop/install-crossover-standard-6.0.0.sh
sh: Can't open /home/toby/Destop/install-crossover-standard-6.0.0.sh
toby@toby-desktop:~$ chmod a+x /home/toby/Destop/install-crossover-standard-6.0.0.sh
chmod: cannot access `/home/toby/Destop/install-crossover-standard-6.0.0.sh': No such file or directory
toby@toby-desktop:~$

---

### Post by Tobster on 2007-02-24
I need to get away from this before I end up going crazy. I e-mail the company that makes cross over and they going to get back to me.

Novell really need to make it easier to install universal software. Conical and other Linux providers   I believe really need to get on there case.

At the end of the day for Ubuntu to exceed install software really should be a two step process something like click on "install" then "OK"

As users it should be overcome with fear everytime you get software that not in Synaptic Package Manager

Toby

---

### Post by Maestro23 on 2007-02-24
> **Tobster said:**
> toby@toby-desktop:~$ chmod +x ShellScript.sh
[COLOR="Red"]chmod: cannot access `ShellScript.sh': No such file or directory
toby@toby-desktop:~$ ./ShellScript.sh
bash: ./ShellScript.sh: No such file or directory[/COLOR]
toby@toby-desktop:~$ sh /home/toby/Destop/install-crossover-standard-6.0.0.sh
sh: Can't open /home/toby/Destop/install-crossover-standard-6.0.0.sh
toby@toby-desktop:~$ chmod a+x /home/toby/Destop/install-crossover-standard-6.0.0.sh
chmod: cannot access `/home/toby/Destop/install-crossover-standard-6.0.0.sh': No such file or directory
toby@toby-desktop:~$

Did you not read my post.  "Shellscript.sh" was the example.  Your filename goes there.

---

### Post by Tobster on 2007-02-24
Do I need to paste that in the terminal, which I did

---

### Post by Tobster on 2007-02-24
sorry could you just write what i need and I just copy and paste it  :)

I think you wonted me to include that code with another code right?

---

### Post by Maestro23 on 2007-02-24
> **Tobster said:**
> Do I need to paste that in the terminal, which I did

Ok. Open a terminal.  I want you to change directories until you get to your Desktop.

> cd /home/toby/Desktop

ls (lower case L)


*You should see your installer file, if that is where you downloaded it to. Next type:

> sh install-crossover-standard-6.0.0.sh

Come back and post what happens.

---

### Post by Tobster on 2007-02-24
chmod: missing operand after `+xinstall-crossover-standard.sh./install-crossover-standard.sh'

---

### Post by Maestro23 on 2007-02-24
> **Tobster said:**
> chmod: missing operand after `+xinstall-crossover-standard.sh./install-crossover-standard.sh'

Ok, now type:

> chmod a+x install-crossover-standard.sh

./install-crossover-standard.sh


What happens?

---

### Post by borris.morris on 2007-02-24
> **Tobster said:**
> Do I need to paste that in the terminal, which I did

Your taking our posts too literal, replace the location with yours. Did you try the sh one? Also, one help, if you press "tab" while in a terminal it will almost always complete what your typing. For example, if I did, ```
cd /ho"tab"
``` it would finish the "/home" for me. Unless you have something else that also starts with ho, then it would output both. It should help reduce your typing & become more accurate.

---

### Post by Tobster on 2007-02-24
:)

Thankyou I have exceeded it's only 0.41am lol

I hope that we could keep in contact as your help really means alot to me.

Is there somewhere where I could learn this code stuff.  

I not sure what programming language Ubuntu uses but I sure would like to know and use it.

Thanks 

Toby

---

### Post by Maestro23 on 2007-02-24
> **Tobster said:**
> :)

Thankyou I have exceeded it's only 0.41am lol

I hope that we could keep in contact as your help really means alot to me.

Is there somewhere where I could learn this code stuff.  

I not sure what programming language Ubuntu uses but I sure would like to know and use it.

Thanks 

Toby

Thank the Ubuntu Gods and all that helped in this thread.:)   Please go back to your first post and edit it to say "RESOLVED".

Glad we could help. Remember to read the documentation.  Mark what you learned hear today and get some sleep.:guitar:

---

### Post by Tobster on 2007-02-24
Ubuntu is great,  I just need to learn codec

Sorry for being a stress head

---

### Post by Gerard Barberi on 2007-02-24
> **Tobster said:**
> Ubuntu is great,  I just need to learn codec

Sorry for being a stress head

Yes, it's very beneficial to learn the commands.  Try researching on the internet for "bash" or a book maybe.  I tried looking myself, but I couldn't seem to find one that looked like a good starter.  

Perhaps someone can recommend one?

---

### Post by borris.morris on 2007-02-25
Good intro and the like about it as well as the commands [here.]("http://www.linuxcommand.org/learning_the_shell.php")
Oh, and I'm no Ubuntu God. Just a 14 year old messing around with Linux.:rolleyes:

---

