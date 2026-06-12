---
title: "Creating Virtual hosts"
date: 2008-05-28
forum: General Help
---

### Post by guitarman on 2008-05-28
Hi, sorry for the newbie question but I looked around and saw so much docs on the subject but am a little stuck on which conf file I  should use?  I am currently hosting a web site and it works fine.  I redirect the domain using an online DNS redirection. Easy right?  I just want to add a second virtual host to this server so that I can host my kids soccer site.  Do I modify the apache2.conf file or other?

Currently, my main site run from /var/www, but I think that it would be best that I create a directory for each site, therefore:

/var/www/main/

/var/www/soccer/

If so what would the virtual host config lines be?  By the way I redirect port 80 on port 8000 and my router redirects the 8000 back to 80 on the LAN side towards my Ubuntu web server.

thanks!
:confused:

---

### Post by ikkubus on 2008-05-28
try adding new entry in vhost.conf under ur apache2 location..

---

### Post by fsmithred on 2008-05-28
This set of directions corresponds to the arrangement of config files in debian/ubuntu. 


[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)
Basic Settings

This section explains Apache2 server essential configuration parameters. Refer to the Apache2 Documentation for more details.

    *

      Apache2 ships with a virtual-host-friendly default configuration. That is, it is configured with a single default virtual host (using the VirtualHost directive) which can modified or used as-is if you have a single site, or used as a template for additional virtual hosts if you have multiple sites. If left alone, the default virtual host will serve as your default site, or the site users will see if the URL they enter does not match the ServerName directive of any of your custom sites. To modify the default virtual host, edit the file /etc/apache2/sites-available/default. If you wish to configure a new virtual host or site, copy that file into the same directory with a name you choose. For example, sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mynewsite Edit the new file to configure the new site using some of the directives described below...

---

### Post by mbeach on 2008-05-28
For my needs I found using /var/www not the best place for placing the subdirectories containing your websites.

What I do is create a folder in my home for all the websites I'll be dealing with.  So you might end up with 
/home/guitarman/sites/kidssoccer.com/
/home/guitarman/sites/guitartutorials.com/

etc etc...

then in your 
/etc/apache2/sites-available folder, create a conf file for each site you'll be dealing with.  So you might end up with
/etc/apache2/sites-available/kidsoccer.com
/etc/apache2/sites-available/guitartutorials.com

I'd start with making copies of the default file that is in there and adjust as necessary:
cp default kidsoccer.com
then edit kidsoccer.com, and be sure to change the ServerName, the Document root which in this example would be 
DocumentRoot /home/guitarman/sites/kidssoccer.com
The ServerName would be like:
ServerName [www.kidssoccer.com](www.kidssoccer.com)
You may want to add a ServerAlias which I believe eliminates the need for the 'www' (good for those on mobile phones etc):
ServerAlias kidssoccer.com *.kidssoccer.com
(I'm not too familiar with the ServerAlias)

you'll also want to be sure to adjust the <Directory /home/guitar/man/sites/kidssoccer.com/ > as needed for your site.  Work with the defaults until you find you need to be using fancier features.  You can also have a special log per site etc, but that stuff is up to you.

Once you have that conf file in /etc/apache2/sites-available, you'll need to tell Apache that you want to enable that site.  Do do so use the following at the terminal (sudo may be required):
a2ensite kidsoccer.com
which creates a symbolic link in 
/etc/apache2/sites-enabled

see [http://diablo.ucsc.edu/cgi-bin/man/man2html?a2ensite+8](http://diablo.ucsc.edu/cgi-bin/man/man2html?a2ensite+8)
for the man page.

If you have /var/www holding your "main" site, you can leave the files there, but adjust a conf file in /sites-available accordingly.  I think if you simply edited the Default file to ensure it uses /var/www then you should be alright.

I think after enabling the site, you may need to tell apache2 to reload the configuration (the message will tell you how).

One thing you may find is that testing becomes problematic.  I've had to adjust my host file 
Windows: C:\WINDOWS\system32\drivers\etc\hosts 
Linux: /etc/hosts
to have the domain point to the ip.  When testing on the local machine where you used to go to 127.0.0.1, you'll now want to be using the domainname so apache can know which virtual host you are wanting to hit (because both now reside on the localhost).  If your DNS service is not up and running or you have some local loopback issues, having the domain and ip in your hosts file may help out.  To continue the example the new additional line in the windows hosts file would like: 
127.0.0.1       kidssoccer.com

this is all from memory, so I likely gave some wrong path here or there.  Hopefully not.

---

### Post by guitarman on 2008-05-28
Hi all,
I followed the instructions and copied the default file in /etc/apache2/sites-available to a new file called soccer and modified it to the follow (by the way brossard is just the name of the city the kids play at):

NameVirtualHost *
<VirtualHost *>
        ServerAdmin [email]info@brossardsoccer.com[/email]
        ServerName *.brossardsoccer.com
        ServerAlias brossardsoccer.com *.brossardsoccer.com
        DocumentRoot /var/www/soccer
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/soccer/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>



Then I did a:
sudo a2ensite soccer
and I got:
Site soccer installed; run /etc/init.d/apache2 reload to enable.




when I went to reload apache, it gave me the following:

 /etc/init.d/apache2 reload
 * Reloading apache 2.0 configuration...                                                                                      [Wed May 28 22:21:54 2008] [warn] NameVirtualHost *:0 has no VirtualHosts
httpd not running, trying to start
(98)Address already in use: make_sock: could not bind to address [::]:8081
no listening sockets available, shutting down
Unable to open logs


What am I missing here? and once it reloads correctly, do I need to configure any other file before apache2 will be able to display this soccer website?  Again, I will be doing a masked domain name forwarding to an online dynamic dns that will repoint to my Ubuntu web server.

thanks again!

---

### Post by mbeach on 2008-05-29
if you still have the Default file in /etc/apache2/sites-available, and it is also still enabled (symbolic link exists in the sites-enabled), you probably don't need the line 
NameVirtualHost *
as it should get Defined by the Default conf file already.
see 
[http://ubuntuforums.org/archive/index.php/t-312916.html](http://ubuntuforums.org/archive/index.php/t-312916.html)
for a reference.  That should get rid of the warning

One thing to note - and I think that Ubuntu names the link to Default as 000-Default already, the conf files are loaded alphabetically - maybe make sure its named so that it gets loaded first (regardless, it should be if you've got default and soccer).

The other part (httpd not running, trying to start) indicates that the apache server is not already running.  You might want to try a 
sudo /etc/init.d/apache2 restart
or
sudo /etc/init.d/apache2 start
not sure why it would try to bind to 8081.  You might have some residual of previous efforts in the /etc/apache2/apache2.conf
I'd take a look there and see if you've attempted to set anything to 8081.  You may also want to look in /etc/apache2/ports.conf
You should likely only need one line in there like:
Listen 80

after all that, try the 
sudo /etc/init.d/apache2 restart
and see how it goes.

---

### Post by guitarman on 2008-05-29
Thanks mbeach,
your advise worked great.  I commented out the line NameVirtualHost * in the /etc/apache2/sites-available/soccer and removed the reference to listen 8081 in ports.conf and restarted apache2 without any errors.

I also did my redirection from godaddy (where I registerd the domain) and pointed it to my online dyndns provider.  Again my online dyndns provider now redirects this to my ISP provided IP address to port 8000 and my router forwards this again to port 80 on the lan side.  The only problem is that the only site that shows up is my original realestate site that I had and not the soccer site. Try it [www.brossardsoccer.com](www.brossardsoccer.com) and see what you get.

My original site is in the /var/www directory and the soccer site is in /var/www/soccer directory. Is the default file under sites-available defaulting everything to /var/www/index.html ? I also put a ServerName statement in the default file to reflect my original realestate site but that did not change anything.

thanks

---

### Post by lotsofish on 2008-05-29
I don't think it's working right. It looks to me like it's using the Free Hosting Account that GoDaddy gives you when you buy a domain name, instead of forwarding to your dyndns domain.

Check your GoDaddy domain forwarding settings again.

---

### Post by guitarman on 2008-05-29
Yes lotsofish, your right. but that is because I just did the mask forward and godaddy take a little while before it is activated. If you go to:

brossardsoccer.no-ip.com (my online dyn dns) 

you'll see what I mean.

I have to type:

brossardsoccer.no-ip.com/soccer

for it to work and go to my site (that I am still working on - only did a few pages :KS).

thanks for catching this.

---

### Post by lotsofish on 2008-05-29
Instead of using brossardsoccer.com in your /etc/apache2/sites-available/soccer file, try brossardsoccer.no-ip.com

```

ServerName brossardsoccer.no-ip.com
ServerAlias brossardsoccer.no-ip.com *.brossardsoccer.no-ip.com

```

---

### Post by guitarman on 2008-05-29
Lotsofish
Thanks again, in fact I had both 

ServerName *.brossardsoccer.com
ServerName brossardsoccer.no-ip.com

but did not have the ServerAlias:

ServerAlias brossardsoccer.no-ip.com *.brossardsoccer.no-ip.com

I added your ServerAlias and removed all others that referred simply to brossardsoccer.com and restarted apache2.  Then I tried to access the site again via an internet proxy, and got the same result.  I always get my default real estate site unless I add the /soccer at the end of the URL.  I thought that apache2 was suppose to see the header and redirect the URL request to the appropriate sub-directory.
 
Can you try it out and tell me if you see the site properly?  It still does not seem to work.

Thanks

---

### Post by lotsofish on 2008-05-29
No it's not, but I think I see why. Your DocumentRoot needs to have a trailing /.

So...
DocumentRoot /var/www/soccer/

You can also drop all the brossardsoccer.com entries, that's not how it will be forwarded. GoDaddy doesn't actually forward your URL, it loads the URL you specify in a frame.

I would simplify your servername/serveralias lines. All you really need is
ServerName brossardsoccer.no-ip.com

The *.brossardsoccer.no-ip.com isn't really necessary, because if you wanted to set up a subdomain, you would probably want a different DocumentRoot again anyway.

Make sure you restart apache everytime you make a change to the sites.

---

### Post by guitarman on 2008-05-30
Good morning all,
Lotsofish, I did the changes you recommended, but my default real estate site still show up when I point to brossardsoccer.no-ip.com .  I still need to use the following to access the soccer site:

brossardsoccer.no-ip.com/soccer 

Attached is my soccer virtual host file from the sites-enabled directory; does anything jump out as obviously wrong? I'm hoping to have this up and running by the weekend so that I can tell the parents about it - any help would be greatly appreciated. Thanks
:confused:


#NameVirtualHost *
<VirtualHost *>
        ServerAdmin [email]info@brossardsoccer.com[/email]
        ServerName brossardsoccer.no-ip.com
        ServerAlias brossardsoccer.no-ip.com *.brossardsoccer.no-ip.com
        DocumentRoot /var/www/soccer/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/soccer/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

---

### Post by mbeach on 2008-05-31
To eliminate godaddy as the source of the problem, I'd make sure it all works properly locally.

I would recommend editing your hosts file (paths described above) and your conf files on your local machine, and attempt from your browser.  Your local machine will typically look to the hosts file for a DNS lookup (that's how I think of it anyway), and if it finds a match, doesn't bother going any further up the chain.  

So if it finds brossardsoccer.com pointing to the proper address 127.0.0.1 (assuming its all on the same machine, use your LAN ip for your apache machine otherwise), then your browser will pass along that "www.brossardsoccer.com" to the apache server, who looks to see if there is a ServerName with *.brossardsoccer.com" and serves it up accordingly, otherwise it will serve up the default.

Do the same for your realestate page locally, to ensure it works properly.

If it does all work fine locally (if it doesn't - post back here - we'll get it sorted out), then concentrate on godaddy's setup - this is where the apache logs should come in handy to see what is being requested.  I use netfirms for all my stuff and have never had to deal with the dynamic ip issue so can't advise too well on that.  Are you using [www.dyndns.com](www.dyndns.com) services?

On a separate note, I would strongly recommend creating another sub directory under /var/www for your real estate site files.  You'll end up with /var/www/soccer and /var/www/realestate.  Then amend the /sites-available/default conf file accordingly and issue the reload (sudo /etc/inet.d/apache2 reload).  Keeping them separate will likely save you some time in the future, especially if you have to move one site to another server etc.  Once you have it all working, and become the local goto guy for setting up the your neighbourhood's watch site, kids basketball schedule site etc, having a clean setup will save loads of time (my experience anyway).  Also if you end up using a cms or other web assistance tool (typolight, django, drupal etc...) having that soccer as a sub directory of your main site might give you some grief.  It might not but I'd do it now while its all 'fresh' in the memory.

---

### Post by guitarman on 2008-05-31
Thanks mbeach, here's the deal.  I'll let you know what I have set up now since I made some changes from yesterday.  Both of my sites (pinatano.com and brossardsoccer.com) are register with GoDaddy and both are masked forwarded to no-ip.com which redirects it back to my personal web server on port 8000 since my cable ISP blocks 80.  My router reroutes the URL request back on port 80 internally towards my Ubuntu web server.  Works great for pinatano.com .  The other site brossardsoccer.com also gets redirected, but pinatano.com is the only one that shows up.  

So to clean up my machine I created 2 sub directories and copied my respective web site files into - ie:

/var/www/pinatano  and
/var/www/brossardsoccer

I also made the changes in the 2 files under /etc/apache2/sites-available.  Please see attachment.  First one is the default file and the second I called brossardsoccer.com.

----------------------
default file:
----------------------

NameVirtualHost *
<VirtualHost *>
        ServerAdmin [email]info@pinatano.com[/email]
        ServerName pinatano.com
        ServerAlias *.pinatano.com
        DocumentRoot /var/www/pinatano
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/pinatano>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


-------------------------
brossardsoccer.com file
-------------------------
#NameVirtualHost *:80
<VirtualHost *>
        ServerAdmin [email]info@brossardsoccer.com[/email]
        ServerName brossardsoccer.com
        ServerAlias *.brossardsoccer.com
        DocumentRoot /var/www/brossardsoccer
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/brossardsoccer>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


My /etc/hosts file contains the following:

127.0.0.1 localhost ubuntu-web1
127.0.1.1 ubuntu-web1

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Hopefully with all this detail you may be able to see what parameter I am missing to make this work.
I'll check back later.  thanks,

---

### Post by mbeach on 2008-05-31
@lotsofish
I've always not had a trailing slash in the DocumentRoot but included one in the Directory directive.  Not sure if that's absolutely correct, but its how I've done it.
From 
[http://httpd.apache.org/docs/2.0/mod/core.html#documentroot](http://httpd.apache.org/docs/2.0/mod/core.html#documentroot)
> The DocumentRoot should be specified without a trailing slash.

I never know exactly what to do in the case of the Directory directive - looking at my files, I am inconsistant on that one.
[http://httpd.apache.org/docs/2.0/mod/core.html#directory](http://httpd.apache.org/docs/2.0/mod/core.html#directory)

@guitarman
lets assume you have one machine on your network, and you are sitting at it.  This machine is the one hosting the Apache service.  Temporarily, I'd add 
> 127.0.1.1 brossardsoccer.com  after the 127.0.1.1 ubuntu-web1 line.  Then, using your browser on that same machine, goto brossardsoccer.com and see which page gets served up.

If you are on some other machine on the same network, lets say its a windows box, you would change the windows host file to have line like
192.168.1.155	  brossardsoccer.com
(substituting 192.168.1.155 with the local ip of the ubuntu machine with apache).  Browse to brossardsoccer.com and see what you get.

mb.

---

### Post by guitarman on 2008-05-31
mbeach,
Added the entry in to the host file and tried it from my web server and it still goes to my realestate page.  Also tried it from another 2 different machines on my lan - one being another ubuntu desktop machine and the other my WinXp laptop.,,, same deal. Also tried it from my kids Vista machine and same thing.

One question comes to mind:  if my realestate site is set on the default file under sites-available and 000-default under sites-enabled, should I be creating a new virtual host file name say pinatano (copied from default) and blow away the default and 000-default files.  My understanding is that apache2 by default starts loading the virtual hosts in alphabetical order.  If this is the case then would it end up loading brossardsoccer before pinatano? Then I would have the opposite happen where the pinatano would default to brossardsoccer.  I'm I off track here?  if I'm only hosting 2 sites, how many files should I have in the sites-available and sites-enabled directories?

before I was able to go type brossardsoccer.no-ip.com/soccer and I was able to at least see the site. This, I'm thinking is because my main site pinatano.com (default file) was under /var/www and I had created a directory /var/www/soccer for my brossardsoccer site. So I'm thinking that apache2 defaulted to /var/www and then we would see any other site under subdirectories if it was in the URL. Now that I created a seperate directory for both sites (as mentioned above) I'm thinking that apache2 defaults to the /var/www/pina and when asking for brossardsoccer.no-ip.com/brossardsoccer it never finds this directory since it's located in /var/www.

making sense? 
thanks

---

### Post by mbeach on 2008-05-31
couple of points.  after changing the conf files, issue the 
sudo /etc/init.d/apache2 reload
command to get the changes to take effect.

the alphabetical loading order is correct I believe.  The order is how they are named in sites-enabled.  You can have a gazillion conf files in sites-available, and in your particular case only 2 should be in sites-enabled.  This setup allows one to disable sites easily (as the hoster waits for payment for example) and subsequently re-enable.  In your case, you should likely have 2 files in each available and enabled.

since in sites-enabled, you've got the symbolic link named 000-default, it should be loading before brossardsoccer, but its worth a shot if nothing else seems to be working (I wouldn't though).  You are dealing with a live site there I think so I'd urge caution in 'blowing away the default'.

As an example, I don't have any sites in /var/www.  You can place the site's files pretty much anywhere you have write access.  I have all our sites I deal with in folders in my home directory.  I've left my original 000-default named as it was, but set the DocumentRoot and directories appropriately.

In your situation you should have (I name them with the .com as I 've got a few .ca etc and like to keep them straight)
.../sites-available/brossardsoccer.com
.../sites-available/pinatano.com

.../sites-enabled/000-default -> .../sites-available/pinatano.com
.../sites-enabled/brossardsoccer -> .../sites-available/pinatano.com

As I see it the pinatano.com file should contain:
ServerName [www.pinatano.com](www.pinatano.com)
DocumentRoot /var/www/pinatano 
<Directory /var/www/pinatano/>

the brossardsoccer.com file should contain:
ServerName [www.brossardsoccer.com](www.brossardsoccer.com)
DocumentRoot /var/www/soccer
<Directory /var/www/soccer/>


By the way though, when I browse to [http://yourip:8000/soccer](http://yourip:8000/soccer) I get "The requested URL /soccer was not found on this server" but the realestate site comes up fine at [http://yourip:8000/](http://yourip:8000/)

---

### Post by guitarman on 2008-05-31
Dude,
here's the latest....  In order to make it work so-so I copied the pinatano.com website files back to the /var/www directory and left all the brossardsoccer.com website files in the /var/www/soccer directory, made the changes in the default file under sites-available and reloaded apache2. 

At least now when I type [www.pinatano.com](www.pinatano.com) I get the cute realestate agent and in order to get my soccer site I have to append a /soccer at the end, therefore [www.brossardsoccer.com/soccer](www.brossardsoccer.com/soccer) or brossardsoccer.no-ip.com/soccer. 

For some reason Apache2 does not want to automatically go to the soccer directory when I type the URL.  You try it and tell me what you get.

This has been fustrating and I never had this much problems with apache 1.3 on Linux CentOS where we created all the virtual hosts in one config file. I've had 4 sites running on that server but about 6 months ago I scrapped CentOS for Ubuntu and kept one of the 4 sites (pinatano.com) - the other sites were just for test. Now that I'm ready to add a second valid site on this Ubuntu server I'm having problems! :mad:

I think that it's time to go out club hopping and have a couple of drinks on this Saturday night so that I can think about it.

Cheers,

---

### Post by mbeach on 2008-06-01
Yes, both of those links work fine.

I think lotsofish described it correctly in that godaddy is really just setting up the frame set and using your IP for the frame.  Apache then never sees the request for brossardsoccer, only the request for your ip 74.59.... so it has no idea you are looking for the soccer site.

Very strange though that it wouldn't work locally on your lan after editing the host files.

You can still go the route of having everything in one config file, but I suspect you are going to run into the same issues with the frameset.  

Easy/more expensive solution is to biggie up to a static ip, and point godaddy to it.  

I've toyed around with the situation with my registrar (Netfirms) and an account with dyndns.  It seems I can create a CNAME record which will point to my dyndns url instead of an ip wrapped in a frameset.  Looking at Google's help on the topic for google hosted services, in your situation here's what I would do (keep in mind I've never seen the godaddy control panel, just adopted this from google's help)

[Following stolen more or less from 
[http://www.google.com/support/a/bin/answer.py?hl=en&answer=47610]](http://www.google.com/support/a/bin/answer.py?hl=en&answer=47610])
   1. Log in to your account at [www.godaddy.com](www.godaddy.com).
   2. Open the Domains tab and select My Domain Names. You'll be directed to the Manage Domains page.
   3. Click the domain that you'd like to use 
   4. Click the Total DNS Control And MX Records in the box entitled Total DNS Control.
      Note: Adding entries to the Manage Subdomains section does not create a CNAME record.
   5. Click Add New CNAME Record. If you've already created a CNAME record for the address, click Edit next to the existing CNAME record.
   6. Step 1: For custom URLs enter [www.brossardsoccer.com](www.brossardsoccer.com) as your address, enter www for step one.
      Step 2: As the host name, enter brossardsoccer.no-ip.com:8000 for custom URLs.
      Step 3: Leave as default selection.
   7. Click Continue, and then click Add. If you're editing an existing CNAME record, click Continue and Update. 


I suspect the proper setup of apache's virtual hosts should work in that case, as they seem to with Netfirms/Dyndns combo.  Godaddy might have some issues with setting the www subdomain as a CNAME but I'd try it.  It is one of those things that takes a day or so to propagate.  Adding the port (8000) may also be prohibited.  Luckily my isp does not block port 80.

If, however, the virtual host setup doesn't work locally on your own lan after editing the hosts files, it won't work coming from the WAN.

Good luck,
mb.

---

### Post by guitarman on 2008-06-01
ok thanks Mbeach.  I will give it a try and see if configuring this in GoDaddy will do the trick. I will let you know after I try.

thanks

---

### Post by Distortedgamer on 2008-08-02
First, great walk-throughs, I have it almost worked out. I do have one question though. Whenever I restart Apache2 I get an error message:

```

[warn] _default_ VirtualHost overlap on port 80, the first has precedence
httpd (no pid file) not running
[warn] NameVirtualHost *:80 has no VirtualHosts

```

The only thing that I think of is that I edited my /etc/apache2/httpd.conf file. It is:
```

#ServerName domainA.com

#NameVirtualHost *:80

<VirtualHost *:80>
    ServerName www.domainA.com
    ServerAlias domainA.com *.domainA.com
    DocumentRoot /Website/domainA
</VirtualHost>

<VirtualHost *:80>
    ServerName www.domainB.com
    ServerAlias domainB.com *.domainB.com
    DocumentRoot /Website/domainB
</VirtualHost>

```

Should I clear out the httpd.conf file? Do I need to change both of those to <NameVirtualHost *:80>? Can I have both of those listening on port 80? I want to be able to access them just by going to domainA.com in the browser.

I have just changed the DNS A records to point to the server IP and waiting for them to propagate and then I am going to test it with those VirtualHost and port overlap errors. 

I would greatly appreciate any help or advice. Thanks in advance!

---

### Post by Distortedgamer on 2008-08-02
Ok well the DNS A records propagated and with the httd.conf file the way it is mentioned above, along with all of the errors (minus the (no pid) error), it kind of works. When I go to [http://domainA.com](http://domainA.com) it brings up the index.html page in /Website/domainA. When I go to [http://domainB.com](http://domainB.com) then it brings up the index.html in /Website/domainA. 

When I comment out EVERY line in the httpd.conf file then both sites go to index.html in /Website/domainB. 

In apache2/sites-available I have *default, domainA.com, domainB.com, domainA.com.back domainB.com.back*

In apache2/sites-enabled I have *domainA.com, domainB.com*

---

### Post by Distortedgamer on 2008-08-03
The actual domain for domainA is second aplphatbetically to the actual domain for domainB so I think that is why it goes to the domainB folders with the httpd.conf file commented out.

---

### Post by Distortedgamer on 2008-08-03
I fixed it!!! Here is the new httpd.conf file:

```

NameVirtualHost *

<VirtualHost *>
        ServerName www.domainA.com
        ServerAlias domainA.com *.domainA.com
        DocumentRoot /Website/domainA
</VirtualHost>
<VirtualHost *>
        ServerName www.domainB.com
        ServerAlias domainB.com *.domainB.com
        DocumentRoot /Website/domainB
</VirtualHost>

```

---

