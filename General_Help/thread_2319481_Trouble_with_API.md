---
title: "Trouble with API"
date: 2016-04-04
forum: General Help
---

### Post by Ute_Willmore on 2016-04-04
I am new to Ubuntu and virtual machines and all that and I have run into a problem I can't figure out. So I am hoping someone here can help.
I am trying to use an API, but I can't get it to work. I get either a 404 error, or 500 General System error. I am pretty sure the problem is related to some configuration in Apache2. I am running Ubuntu as a VirtualBox on a Windows 8 system.

I had to install a few things just to get the API install, such as composer and Flight. Part of the Flight installation was to create an .htaccess file, and for the longest time I could not figure out to allow access to that file, and I am still not sure if I got it right. But, right now, the ,htaccess file in in my shared directory, and so are the file needed for the API. I had everything in a sub directory but could not get passed the 404 (page not found) error. 
I changed my apache2.conf file to include this

<Directory /media/sf_vm/www>
  AllowOverride All
</Directory>

/media/sf_vm/www is my  shared directory. 
My .htaccess file looks like this:

RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ index.php [QSA,L]

I checked and it looks to me as if rewrite is enabled. At least there is a rewrite.load file in /etc/apache2/mod-enabled.

The code is installed in /media/sf_vm/www and that's were the .htaccess file is located too. 

My shared folder is also my root directory for the virtual server, at least I think so.  When I used the virtual box to work on a web application, I placed the code in the shared directory and then ran in using localhost for the server. Since that brought up my web app, I figure the shared folder is also my web root, right? Anyway, back to the problem at hand.

I installed RestClient, a FireFox Add-On and tried to post a request to [http://localhost/register](http://localhost/register). The post looks like this:

{
    "email": [EMAIL="ute@frii.com"]"ute@frii.com"[/EMAIL],
    "password": "TH1$ I$ @ T3$T P@$$W0rd",
    "repeatPassword": "TH1$ I$ @ T3$T P@$$W0rd"
}

But I get back:
 
    Status Code: 500 Internal Server Error
    Connection: close
    Content-Length: 0
    Content-Type: text/html
    Date: Mon, 04 Apr 2016 18:12:21 GMT
    Server: Apache/2.4.7 (Ubuntu)
    X-Powered-By: PHP/5.5.9-1ubuntu4.11
 

I got the installation instruction and the text for the Post request from the programmer who wrote the API, PHPAuth-API. He has been very helpful but doesn't know much about Apache and had to give up when we got to the point where we realized it had to do with Apache.

At one point I had a subdirectory in the shared folder called PHPAuth-API and had installed everything in that sub-directory, including the .htaccess file. With the same change to apache2.conf and the same post request, I got 


   404 Not Found
   Not Found
   The requested URL /register was not found on this server.
   Apache/2.4.7 (Ubuntu) Server at localhost Port 80

That's why I re-installed directly under the www folder, thinking that maybe the sub-directory was a problem. Well, it looks like removing the sub-directory made a difference all right, but of course it didn't fix things.

Can someone here tell me what I am screwing up? I would really appreciate some help. I've been at this for 4 days now and I am running out of ideas.

Thanks 

URW

---

