---
title: "iFolder: Change default port error"
date: 2008-03-12
forum: General Help
---

### Post by lisdeksia on 2008-03-12
Hi,

iFolder by default uses port 80. I need to change that to port 8080 in our environment. I have read several articles on how to do that, however it does not appear to work. When I restart Apache after the changes, I get the errors pasted below. I also loose the ability to get authenticated in the client(change made: x.x.x.x:8080) or on the web.
I make the port change in the ports.conf file and run the simias,admin and web setup again to specify the new port.
When I do change it back to port 80, all is well again.

Any ideas??

 * Stopping web server apache2                                                  [Wed Mar 12 08:48:33 2008] [crit] (17)File exists: Failed to create shared memory segment for backend 'XXGLOBAL'
[Wed Mar 12 08:48:33 2008] [crit] (17)File exists: Failed to create shared memory segment for backend 'admin'
[Wed Mar 12 08:48:33 2008] [crit] (17)File exists: Failed to create shared memory segment for backend 'ifolder'
[Wed Mar 12 08:48:33 2008] [crit] (17)File exists: Failed to create shared memory segment for backend 'simias10'
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

---

### Post by arcole on 2008-03-12
same issue when i try and login to /admin i get "Unable to connect to the iFolder server."

when i restart apache i get
 * Restarting web server apache2                                                                                              [Wed Mar 12 18:37:56 2008] [crit] (17)File exists: Failed to create shared memory segment for backend 'XXGLOBAL'
[Wed Mar 12 18:37:56 2008] [crit] (17)File exists: Failed to create shared memory segment for backend 'admin'
[Wed Mar 12 18:37:56 2008] [crit] (17)File exists: Failed to create shared memory segment for backend 'ifolder'
[Wed Mar 12 18:37:56 2008] [crit] (17)File exists: Failed to create shared memory segment for backend 'simias10'
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.50 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.50 for ServerName
                                                                                                                       [ OK ]

had no idea to even think about the port being the issue but i also have apache setup for port 8080 so would be nice to know where to change ifolder. 

i will start looking now just thought i would add my 2 cents here if i find anything i will add more going to check ifolders site and more.

---

### Post by arcole on 2008-03-12
found this but it is not working for me still getting the same errors.

[http://www.novell.com/communities/node/4148/changing-listen-port-ifolder-36](http://www.novell.com/communities/node/4148/changing-listen-port-ifolder-36)

---

### Post by lisdeksia on 2008-03-12
Yes, that is one of the documents that I used, but it did not work for me

---

### Post by arcole on 2008-03-12
well i can get the client to connect to the server and sync files and foulders but i just cant access the admin page so i am like half way :confused:

update: i can also login to [http://192.168.1.50:8080/ifolder](http://192.168.1.50:8080/ifolder) with not prob but still cant login to [http://192.168.1.50:8080/admin](http://192.168.1.50:8080/admin)

update: ok i ran
sudo simias-server-setup
sudo ifolder-admin-setup
sudo ifolder-web-setup

and everywhere it asked for url i made sure i put [http://192.168.1.50:8080](http://192.168.1.50:8080) also did the fixes to the conf file like the guide says to after running each
now apache restart looks like this.

 * Restarting web server apache2                                                                                              apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.50 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.50 for ServerName
                                                                                                                       [ OK ]

when i go to [http://192.168.1.50:8080/admin](http://192.168.1.50:8080/admin) above the login it has "iFolder Server: http://192.168.1.50/" before it always said localhost but i still get the same error when trying to connect.

update: ok i got in!!! make sure you check all the config files for the url i found one that did not get updated in /usr/local/lib/simias/admin/Web.config
added the :8080 restarted apache now getting the errors again as it loads. the admin login screen says the ip with the port and i am able to connect.

---

### Post by lisdeksia on 2008-03-13
Hi,

I tried the setup again and you were right, I found a couple of places that the port was not added to the IP address. I am able to login to the iFolder(admin web, ifolder web and client), but on the client the files are not synchronizing. It states that the server is unavailable...making progress though...

Thanks for the help.

---

### Post by arcole on 2008-03-13
> **lisdeksia said:**
> Hi,

I tried the setup again and you were right, I found a couple of places that the port was not added to the IP address. I am able to login to the iFolder(admin web, ifolder web and client), but on the client the files are not synchronizing. It states that the server is unavailable...making progress though...

Thanks for the help.

ya mine did that also a bit after it was running all i did to fix it was restart apache and it was working again.

on a side note it sucks that you can not sync anything in c:/program files/ wanted to use this to also do backups of some things but oh well.

---

### Post by lisdeksia on 2008-03-14
Hi again,

The issue is actually greater than what I thought. Nobody can connect to the iFolder sever through the client. Web access is fine. It appears that the users cannot be authenticated through the client. I must be missing a port entry somewhere?

J

---

### Post by arcole on 2008-03-14
> **lisdeksia said:**
> Hi again,

The issue is actually greater than what I thought. Nobody can connect to the iFolder sever through the client. Web access is fine. It appears that the users cannot be authenticated through the client. I must be missing a port entry somewhere?

J

lol i was going to make a comment on this but just got around to it. i am having the same issue and from what i have found is that ifolder uses a random port when it loads so there is no real way to have it so people can connect. i saw some stuff online where you can put something in the config to make it work with a static port but the info is not working for me. i was so happy to get ifolder working but the more and more i use it i think it is a pointless app unless everyone is on the same lan and even then it has limits on what can and can not be synced. also there is just about no support the website sucks.

i want something that works like this [http://www.getdropbox.com/](http://www.getdropbox.com/) but i can run the server on my system not someone elses.

---

