---
title: "Apache/PHP loosing php.ini settings."
date: 2016-02-10
forum: General Help
---

### Post by kisonay on 2016-02-10
I'm on Ubuntu 14.04 and my server has been running great for about year.

Lately, it seems that ever day apache/php looses my custom config settings and sets the max upload size to 2MB yet in my php.ini file it is set to 500MB.

If I restart apache, the config file is picked up and uploads over 2MB are allow but within 24 hours, its back to the 2MB limit.

Has anyone ever experienced anything like this? It's driving me nuts.

---

### Post by SeijiSensei on 2016-02-10
When you say it is back to the 2 MB limit, does that also mean that php.ini has been changed back to that setting as well?  If so, there must be some script somewhere that is doing that.  I've run Apache with PHP for many years now and have never seen this problem.

Are you running CMS applications like WordPress, Drupal, or Joomla?  Any chance the problem lies with one of them?

If php.ini is in fact being changed, you can keep that from happening while you search for the source of the problem by making the file "immutable" like this:
```
sudo chattr +i /etc/php5/apache2/php.ini
```
Now no one, not even root, can make changes to the file.  You'll need to run the same command with "-i" before editing php.ini in the future.

---

### Post by kisonay on 2016-02-10
> **SeijiSensei said:**
> When you say it is back to the 2 MB limit, does that also mean that php.ini has been changed back to that setting as well?  If so, there must be some script somewhere that is doing that.  I've run Apache with PHP for many years now and have never seen this problem.

actually the php.ini file is untouched. All that I run is ```
sudo service apache2 restart
``` and the config is picked up again.

---

### Post by SeijiSensei on 2016-02-10
Create a file in the main website directory called info.php with just this line:
```
<?php phpinfo() ?>
```
Next time the limit appears to recur open this file from a browser and see what it shows for the  max upload size setting.

It's highly implausible that the server would just reset on its own.  Are you uploading via a custom script you wrote, or is it part of a suite like WordPress?  If the former, can we see the script including the HTML form that handles the upload?

---

### Post by kisonay on 2016-02-11
> **SeijiSensei said:**
> Create a file in the main website directory called info.php with just this line:
```
<?php phpinfo() ?>
```
Next time the limit appears to recur open this file from a browser and see what it shows for the  max upload size setting.

It's highly implausible that the server would just reset on its own.  Are you uploading via a custom script you wrote, or is it part of a suite like WordPress?  If the former, can we see the script including the HTML form that handles the upload?


Sure enough, it happend again today. The phpinfo is indicating that there is a 2M limit. When I run ```
sudo service apache2 restart
``` and refresh the phpinfo page it then shows the 500M it should.

I don't modify any files or change anything I only restart apache.

---

### Post by SeijiSensei on 2016-02-11
Is this really "your" server or one that is hosted by a provider?  All I can think of is that you have a virtual server or some co-located server, and the provider imposes the 2M cap when it discovers machines are using a larger number.  If php.ini remains unchanged, but the phpinfo report says it has been reduced back to 2M, then some outside agent must be involved.  

As I asked before, are these uploads being handled by a script you wrote, or by some third-party software?

---

### Post by kisonay on 2016-02-12
> **SeijiSensei said:**
> Is this really "your" server or one that is hosted by a provider? All I can think of is that you have a virtual server or some co-located server, and the provider imposes the 2M cap when it discovers machines are using a larger number. If php.ini remains unchanged, but the phpinfo report says it has been reduced back to 2M, then some outside agent must be involved. 

As I asked before, are these uploads being handled by a script you wrote, or by some third-party software?

I appreciated your time in responding. 

Sorry, I missed that original question, the uploads are handled through a third party application and as I mentioned, they have been working fine for the past year, just over the past week something has changed. It is on a unmanaged VPS (I handle all settings and installations, there are no limits or provider imposed limits.)

When it happened again today, I did some comparing with the phpinfo() before and after the restart and noticed something interesting.

before the restart the "Loaded Configuration File" location is /php.ini but when I go to the root of the server said file doesn't exist. Once I restart apache, the location updates to /etc/php5/apache2/php.ini which is what I would expect.

Is there a log file that could shed some light on this?

---

### Post by SeijiSensei on 2016-02-12
Look in /var/log/apache2 for the logs.  The error.log might be helpful.

Is there a /php.ini?  Did you put it there?  Try renaming it, then creating a symlink with
```

cd /
sudo ln -s /etc/php5/apache2/php.ini

```

---

### Post by kisonay on 2016-02-19
> **SeijiSensei said:**
> Look in /var/log/apache2 for the logs.  The error.log might be helpful.

Is there a /php.ini?  Did you put it there?  Try renaming it, then creating a symlink with
```

cd /
sudo ln -s /etc/php5/apache2/php.ini

```

SeijiSensei, I appreciate your guidance.

there was no php.ini file at the root so I created the symlink. Today I looked at phpinfo() and sure enough, it reset to /php.ini again but looking at the settings the symlink was successful and all of the settings found at /etc/php5/apache2/php.ini are being used.

At least I have it working, now I just need to figure out why it is happening nightly. Again, than you for your time and help with this.

---

### Post by SeijiSensei on 2016-02-19
You're welcome.

Let us know what your investigations reveal.  This is such an unusual problem that it must have an unusual answer.

---

