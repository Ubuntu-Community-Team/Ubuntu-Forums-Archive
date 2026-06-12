---
title: "How do I retrieve a stored password from the gnome keyring?"
date: 2013-03-15
forum: General Help
---

### Post by stinkeye on 2013-03-15
I've been binding an xdotool command to a mouse button to type my password 
but thought I might try making it more secure by storing the password in the keyring 
and retrieving it to be used in the xdotool command.

ie
the xdotool command types my password and hits enter.
```
xdotool key --delay 50 [COLOR="#FF0000"]P A S S W O R D[/COLOR] Return
```

I want it to be like this...
```
xdotool key --delay 50 `[COLOR="#FF0000"]command to retrieve password from keyring[/COLOR]` Return
```
...but don't know how to retrieve a stored password from the keyring.

---

### Post by schragge on 2013-03-15
Not sure I understand what keyring you mean, but there are python modules to access system keyrings like Gnome-keyring and KWallet from python scripts: python-keyring, python-gnomekeyring, python3-keyring. Besides, there's [nss-passwords](http://manpages.ubuntu.com/manpages/precise/en/man1/nss-passwords.1.html) to read passwords from Mozilla products.

---

### Post by stinkeye on 2013-03-15
I don't understand much about passwords and keyrings.
It's a password I added under the login section in seahorse.
I don't understand python or any code, except simple bash.

Just wondered if there was a simple command line way to access the
password I added or does it need to be done in a python script?

---

### Post by stinkeye on 2013-03-15
ok, thanks.
 I found this [**_[COLOR="#B22222"]python script[/COLOR]_**]("https://github.com/kparal/gkeyring") described as...
> A small Python tool for shell access to GNOME keyring. It provides a simple way to query and create keyring items.

Seems to do as I want.
I can use it to add a password to gnome keyring and also retrieve.
When I add with something like this, it then asks to put in the password to be saved.
I put the password in and then it outputs an ID.
```
glen@Quantal:~$ gkeyring --set -n mylogin -p mylogin=1
Password: 
12
```

Then to retrieve...
```
gkeyring --id 12 --output secret --no-newline
```

I googled for a sed script to put spaces between the characters of a string 
so when used with xdotool it would recognize the output as individual characters.
eg
```
xdotool key --delay 50 `gkeyring --id 12 --output secret --no-newline | sed 's/./& /g'` Return
```

Now,using easystroke, I have a spare mouse button to autoType my password whenever authentication is required...including the lockscreen.
Not really needed...I just wanted to see if it could be done. 8-[

---

### Post by sudodus on 2013-03-16
> **stinkeye said:**
> ok, thanks.
 I found this [**_[COLOR=#B22222]python script[/COLOR]_**]("https://github.com/kparal/gkeyring") described as...


Seems to do as I want.
I can use it to add a password to gnome keyring and also retrieve.
When I add with something like this, it then asks to put in the password to be saved.
I put the password in and then it outputs an ID.
```
glen@Quantal:~$ gkeyring --set -n mylogin -p mylogin=1
Password: 
12
```

Then to retrieve...
```
gkeyring --id 12 --output secret --no-newline
```

I googled for a sed script to put spaces between the characters of a string 
so when used with xdotool it would recognize the output as individual characters.
eg
```
xdotool key --delay 50 `gkeyring --id 12 --output secret --no-newline | sed 's/./& /g'` Return
```

Now,using easystroke, I have a spare mouse button to autologin whenever authentication is required.
Not really needed...I just wanted to see if it could be done. 8-[

Interesting :-)

I tried ***gkeyring*** and it works for me too. I made the following mini-script to view all my 'secrets' alias passwords in this keyring.
```
i=0;while true; do i=$(($i+1));python gkeyring.py --id "$i" -o id,secret,name||break;done
```

It works when logged into the desktop with 'my own user id'. I tested the security: if it would work from another user, but I did not manage to do that. Then I found that ***it does not work with my own user, when logged in via ssh*** from another computer in the LAN. I have looked into the python script, but have to admit, that I don't understand it.

How come it won't work via ssh? I also found that ***Seahorse*** finds the gpg keys, but not these 'secrets' alias passwords via ssh (while it finds everything when logged into the desktop). Is it designed to be like that or a bug?

---

### Post by stinkeye on 2013-03-16
> **sudodus said:**
> Interesting :-)

I tried ***gkeyring*** and it works for me too. I made the following mini-script to view all my 'secrets' alias passwords in this keyring.
```
i=0;while true; do i=$(($i+1));python gkeyring.py --id "$i" -o id,secret,name||break;done
```

It works when logged into the desktop with 'my own user id'. I tested the security: if it would work from another user, but I did not manage to do that. Then I found that ***it does not work with my own user, when logged in via ssh*** from another computer in the LAN. I have looked into the python script, but have to admit, that I don't understand it.

How come it won't work via ssh? I also found that ***Seahorse*** finds the gpg keys, but not these 'secrets' alias passwords via ssh (while it finds everything when logged into the desktop). Is it designed to be like that or a bug?
Have a look here ...
[**_[COLOR="#B22222"]access keyring over ssh[/COLOR]_**]("https://answers.launchpad.net/gkeyring/+question/209138")

---

### Post by sudodus on 2013-03-16
> **stinkeye said:**
> Have a look here ...
[**_[COLOR=#B22222]access keyring over ssh[/COLOR]_**]("https://answers.launchpad.net/gkeyring/+question/209138")

Yes, this works, and I'm beginning to understand :KS

Thank you :-)

---

