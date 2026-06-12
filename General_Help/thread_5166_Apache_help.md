---
title: "Apache help"
date: 2004-11-16
forum: General Help
---

### Post by Darti on 2004-11-16
I have just installed apache using synaptic and everything went fine with the installation. I have check the httpd.conf settings and they are set as follows:

DocumentRoot /var/www
DirectoryIndex index.htm index.html

I tested the host and got the apache default page, everything looking good at this point.
I then removed everything from the folder apache2-default so it wouldnt show, but when i put a index.html file in to /var/www and go to the host then all i get is a directory listing as follows:

[http://10.0.0.4/apache2-default/](http://10.0.0.4/apache2-default/)

I then thought maybe i had to put the index.htm into the folder /var/www/apache2-default, but still all i get is a directory listing with the index.htm as one of the files listed.

i deleted all cache and tried again, but still no difference. Its the same from the server as well when you load localhost, so it definatelly a config problem. I also did a search for apache2-default in the httpd.conf and found nothing.

This is on a on a single host domain with no virtual hosts.

what am i missing out to make it load the index.htm file?

Please help!

P.s am only just starting to get to know linux so go easy on the technical stuff  :-?

---

### Post by p!=f on 2004-11-16
I've installed Apache2 but I don't experience such a problem. Everything's working like a charm from the default installation.
 
 I didn't delete anything, just created a directory "test" in /var/www and placed simple index.html inside just to see if it works. Finally pointed my browser to localhost/test and voila, it is.
 
 Reinstall Apache2 by
 ```

 sudo apt-get --reinstall install apache2
 
```
 and try similar aproach as mine (don't delete anything).
 
 You should also check the logs.

---

### Post by Darti on 2004-11-16
i have tried that command now but it didnt do anything, still the same problem. 

I have also done a full reinstall of all apache, by removing it first. I then did a test on the site with the defaults still loaded and the apache home page came up no problem, but when i create a new directory in /var/www eg /var/www/site/ and put a index.htm inside of it, then go to localhost/site/ all i get is a directory listing with the index.htm as a listing. the page doesnt load. 

 :-(

---

### Post by jBilbo on 2004-11-18
Just delete:

```
        # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
        RedirectMatch ^/$ /apache2-default/
``` 

In the "/etc/apache2/sites-available/default" file and restart apache.

---

### Post by wiseNoob on 2004-12-04
[QUOTE=jBilbo]Just delete:

```
        # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
        RedirectMatch ^/$ /apache2-default/
``` 

In the "/etc/apache2/sites-available/default" file and restart apache.[/QUOTE]

Darti: since you will probably read this after you have already deleted it...  sorry if you have...

You don't have to delete that.  Just comment it out. Path of least resistance and all that...  it should look like this:

```
        # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
       # RedirectMatch ^/$ /apache2-default/
```

---

### Post by charleyramm on 2004-12-05
I seem to remember ( although not in ubuntu ) having trouble because i used index.htm and not index.html
 i think there is a line in the apache conf that covers this.

---

### Post by dr.diesel on 2004-12-07
Now I installed Apache2 and PHP was after Synaptic Package Manager installation not operable. Then I found out, that with Ubuntu I already had Apache, but Apache1.X, I installed Apache2, but it hadn't started because of Apache1 was started.

So I did

/etc/init.d apache stop
gedit /etc/default/apache2
 - here I wrote 1 instead of after installation default 0
/etc/init.d apache2 start

Then PHP and apache2-default worked, after I commented out the line to go into apache2-default, I get in /var/www with HTTP request.;)

Now my problem is, that I can get here only from localhost, I can't get in with HTTP requests from LAN. Shorewall can be stopped, but still no response :)

P.S. I made
# update-rc.d apache remove
to have apache2 on boot with no socket conflict (port 80 for apache and apache2) started (rc scripts for apache2 are set up by installation)

Anyone have tip for connection from LAN? (Apache1x worked, apache2 doesn't... yet :))) )

Thx 4 great distro.

---

### Post by wiseNoob on 2004-12-07
did you use [http://localhost/](http://localhost/) to get in from lan, or your internal/external IP address?

I had a similar problem, internal IP turned out to work. but not localhost

---

### Post by dr.diesel on 2004-12-07
Ehh, I am a linux newbie, but not IT newbie ;) Localhost is usual hostname of local computer's 127.0.0.1 IP. Of course I tried LAN or net IP of computer (in same ISP LAN)  ](*,)  BTW external and then internal too. Neither worked.

I am going to find out the problem now  :-k

---

