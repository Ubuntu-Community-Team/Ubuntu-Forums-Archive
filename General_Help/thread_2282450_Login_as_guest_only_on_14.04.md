---
title: "Login as guest only on 14.04"
date: 2015-06-14
forum: General Help
---

### Post by shantiq on 2015-06-14
I turned my computer off today and when i tried to start up again
it goes to guest only and does not let me type in my password
when i tried and click on the login box it goes straight into the guest account

I have made no changes whatsoever and fail to understand what is happening

I am on an external SSD   and have been using this for a while and it has been fine

Any ideas what could have changed and how to fix this 


thanx    shan

---

### Post by Steve_Horan on 2015-06-14
Post you the output of the following file:

> /etc/lightdm/lightdm.conf

---

### Post by shantiq on 2015-06-14
it is empty but then i am on a guest login

---

### Post by Steve_Horan on 2015-06-14
Press Ctrl + ALT + F1

Login with your username and password. 

> ls -lah | grep -i xauthority

Make sure your are the owner of this file. If not...

> chown username.username .Xauthority

Also run...

> dpkg-reconfigure lightdm

Press CTRL + ALT + F7 and you should now be able to login.

---

### Post by shantiq on 2015-06-14
thank you Steve   can you explain a bit more in detail please   i do not understand all the detail here

first   do    [COLOR=#000000]Press Ctrl + ALT + F1   then   where does all this go  [/COLOR][COLOR=#000000][I]ls -lah | grep -i xauthority    etc


sorry this is not an area i am familiar with


thanx   shan[/I][/COLOR]

---

### Post by Steve_Horan on 2015-06-14
CTRL + ALT + F1 should present you with the TTY1 command line prompt. You should be prompt to login.

Here you should type your username and password. Now we have logged into a shell as your username.

We should then type the command: 
> [COLOR=#000000]*ls -lah | grep -i xauthority*[/COLOR]

You should see an output to the screen similar to this: 
> horan@horan-laptop:~$ ls -lah | grep -i Xauthority
-rw-------  1 horan horan   57 Jun 14 09:48 .Xauthority


We need to make sure that your user and group permission match **your** username similar to mine here.
> -rw-------  1** horan horan **  57 Jun 14 09:48 .Xauthority

If this same something similar to **root root**. We need to go ahead and correct those by typing:
> chown yourusernamehere yourusernamehere .Xauthority

After this is complete lets reconfigure lightdm (your desktop environment) with this command:
> dpkg-reconfigure lightdm

Then you can go ahread and pres CTRL + ALT + F7 to reload your window manager.

---

### Post by shantiq on 2015-06-14
thank you so much for your time Steve

it says that ls-lah is not found when i run the first command

---

### Post by Steve_Horan on 2015-06-14
Make sure the is a space between ls and -lah \\:D/

---

### Post by shantiq on 2015-06-14
ha 

ok   all went swimmingly this time


just had use     sudo dpkg-reconfigure lightdm     as not happy without sudo      BUT   when i go back F7    still   no way other than guest login

so  what else can one do   ?


and thanx for your help again

---

### Post by Steve_Horan on 2015-06-14
Ok, be can go back to CTRL + ALT + F1 and type:

> mv .Xauthority .Xauthory.bck

Service type:
> service lightdm restart

And head back to CTRL - ALT - F7 and see if we are corrected.

---

### Post by shantiq on 2015-06-14
Thanx for your help Steve   got back in

just with CTRL ALT + F1  in the end then log in with name and password
then    CTRL ALT + F7  and clickin on my name so it gave me access to typing in password   and moved Guest to where it should be


I then reloaded and it was ok second time round

hope it holds


weirdest thing; never seen this before  :]

---

### Post by Steve_Horan on 2015-06-14
Glad I could help.

---

