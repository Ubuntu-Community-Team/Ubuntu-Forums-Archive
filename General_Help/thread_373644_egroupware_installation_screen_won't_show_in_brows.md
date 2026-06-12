---
title: "egroupware installation screen won't show in browser"
date: 2007-03-01
forum: General Help
---

### Post by spacegypsy on 2007-03-01
I installed egroupware with synaptic package manager,

normally when I type 'http://localhost/egroupware' in my browser the installation sreen should appear.

But this time firefox tells me; > Unable to connect Firefox can't establish a connection to the server at localhost.

Why is this?:confused: 

Do I need to install more packages to run egroupware?

thx

---

### Post by spacegypsy on 2007-03-03
Anybody?

I removed egroupware completely and reinstalled it.

Now I get 

> Not Found

The requested URL /egroupware was not found on this server.
Apache/2.2.4 (Unix) DAV/2 mod_ssl/2.2.4 OpenSSL/0.9.8d PHP/5.2.1 mod_apreq2-20051231/2.5.7 mod_perl/2.0.2 Perl/v5.8.7 Server at localhost Port 80

---

### Post by spacegypsy on 2007-03-03
when running sudo apache2 in terminal i get;

> Syntax error on line 19 of /etc/apache2/conf.d/egroupware:
Invalid command 'php_flag', perhaps mis-spelled or defined by a module not included in the server configuration


---

### Post by BadSquishy on 2007-05-22
I just ran into the same problem this morning.  I have a test server with the hostname tester, it's running 6.06 Server Edition.  I installed egroupware this morning with aptitude 
```
sudo aptitude install egroupware
```
During the initial installation it informed me that I was only going to be asked for a header admin username and password, and that the rest of my setup would be completed by pointing a web browser to "http(s)://tester/egroupware/setup".  Next it asked me for the header admin user name and password.  The header admin user name field was pre-populated with the name admin, when I attempted to delete this and type in a different user name it didn't show the characters properly in the field.  I kept going and typed in a password, etc. and everything appeared to go well.  It asked me another couple of questions like which version of Apache I was using (I answered Apache 2) etc.  After aptitude finished I pointed my browser to [http://tester/egroupware/setup](http://tester/egroupware/setup), and lo-and-behold, there was egroupware up and running.  Well, it ran some installation tests, then when I got to the egroupware header admin login screen it wouldn't let me log in (I think because there were some extra characters in the user name I didn't know).  So I figured I'd just purge and re-install egroupware to go through the initial header admin username and password setup again.  

Here comes the real problem.  I ran the command
```
sudo aptitude purge egroupware
```
and it uninstalled the 89 packages it had installed previously.  I immediately ran 
```
sudo aptitude install egroupware
```
Now during the installation it throws the same error seen by spacegypsy
> Syntax error on line 19 of /etc/apache2/conf.d/egroupware:
Invalid command 'php_flag', perhaps mis-spelled or defined by a module not included in the server configuration
Also, it never runs the installation script that tells me where to point my browser, asks for my header admin username and password and asks for which version of Apache I'm running.  

Has anyone else been able to setup egroupware successfully?  I have zero Apache experience and was hoping that Ubuntu would be so slick I could get egroupware up and running even without knowing anything about Apache or PHP.  

Is there a fix for this problem?

Regards,

---

### Post by BadSquishy on 2007-05-23
I found that spacegypsy started another thread on the same topic a couple days later:

[Subject: apache2 syntax error]("http://ubuntuforums.org/showthread.php?t=375190")

This post has more information on things to try to fix the problem, and I got it fixed.  So please check out the other thread.  

Regards,

---

