---
title: "Apache instalation help needed!"
date: 2008-05-01
forum: General Help
---

### Post by voytec on 2008-05-01
Ubuntu is totally new to me. I like it so far but I have a problem with Apache installation. 

I did as it was said in the Ubuntu Help Center:

[COLOR="Red"]sudo apt-get install apache2[/COLOR]

and now it is in the root domain. 
I thought I am a root! But now I do not have permission to change any settings!

Thank you in advance for your help.

---

### Post by Monicker on 2008-05-01
Can you be a bit more specific? 

What are you trying to change, how are you trying to change it, and what error messages are you receiving?

---

### Post by freebeer on 2008-05-01
Apache2 usually installs and runs under the user "www-data".  Because of the nature of the linux file system, you need to grant yourself "root" privileges when working with files not owned by you.  This is normally achieved through the sudo command.

Here's a link that explains it a little more fully (and better than I can): [linky]("http://www.psychocats.net/ubuntu/permissions")

---

### Post by IcemanV9 on 2008-05-02
You did install apache2 as "root" by using sudo ... so, you need to do the same thing by changing settings/options/configuration with sudo! e.g.
```
[COLOR="Orange"]sudo[/COLOR] nano /etc/apache2/httpd.conf
```
BTW, welcome to the wonderful world of Ubuntu Linux. :)

---

### Post by voytec on 2008-05-02
I have my whole web site structure ready. All I need is to copy everything into /var/www 
But I do not have a permission!
What would be sudo command to do that?

OK I have this done so far:

sudo mv /home/user/Documents/*.* /var/www/

But it did not move my folders! I am working on it now :D

I just moved the folders one by one but if there is a command to do this I would like to know it!

Thanks guys!

---

### Post by freebeer on 2008-05-02
```
 sudo cp [location and names of files to copy] [/var/www/] 
```

should do it.  Alternatively, you can use nautilus to copy the files over, but you've first got to give it sudo privileges

```

gksudo nautilus

```

The latter command "gksudo" is used when you want to launch a graphical application with sudo privileges.

---

