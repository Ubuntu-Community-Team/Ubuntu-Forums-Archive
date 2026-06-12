---
title: "Apache 1.3 Tomcat 5.5 and vHosts"
date: 2005-08-25
forum: General Help
---

### Post by docwex on 2005-08-25
Now, i've got a pretty tough problem here and i don't seem to find any help on the net, so here it goes:

I've got a Apache 1.3 Server running with several vHosts pointing to the users home-directory (something like "/home/user/www") and that works fine.
I've also got a running Tomcat 5.5 Server running, which is able to run the example jsp-files.
i do have the mod_jk.so installed but not configured within httpd.conf

What i want to do is allow users to execute .jsp-pages in their own directory and subdirectories, so they can develop their own J2EE-Applications.
The main problem for me is probably, that i have no idea what exactly J2EE is and how it woks, but one of my users wants it, and who am i to deny his wish?

Thanks for any help in advance.

---

### Post by amohanty on 2005-08-25
Without going a bit more deeper into tomcat and J2EE apps it will be very difficult for you to set up things with tomcat. Let me try to put it as simply as possible.

Tomcat Docs: [http://jakarta.apache.org/tomcat/tomcat-5.5-doc/index.html](http://jakarta.apache.org/tomcat/tomcat-5.5-doc/index.html)

Tomcat needs the context path to the apps you deploy to be specified in the server.xml in the conf dir. There you will need to specify the path to the lib dir for every user. The smarter way is to intercept every request using something like a redirector servlet and then setup the context path on the fly. Unfortunately this does not scale very well as you can imagine.

THe best way to go is to find a web application server. JBoss might fit you bill but you will have to look up the docs to see. In short, its kind of hard and will require much reading or much expenditure. Take your pick.

HTH
AM

---

### Post by docwex on 2005-08-26
Thanks for the quick reply.

Yeah, that i figured, since I've been going up and down the Tomcat Docs and i find it kind of hard working with it. So far i've tried via regexp-redirect of .jsp-files in httpd.conf to Tomcat, which works but you have to put your jsp stuff into the Tomcat Webroot.
I've also tried with <host>-directives in the server.xml in combination with the redirect, but couldn't get them configured right, to do what i wanted.

So to sum it up:
a jsp-file gets redirected to Tomact, but Tomcat just looks in its own directory. If somebody could help me change that behaviour, that would allready be of great help.
If Tomcat has the same vHost-capabilities as Apache then it should be possible somehow. I'd be greatful for a little <host></host>-exampletag (or whatever tag) that can do that.

I have absolutely no concern about scalability or performance whatsoever, because this System is for max. 5 Users. It's a development Server i have with the guys i share my flat with and there is barely ever more than two requests at once.

---

### Post by docwex on 2005-08-27
Okay, i got a little further.
i have a rewrite rule for each vhost, that's supposed to be able to use jsp-files just for those who are interested :

<VirtualHost apache_vhost:80>
    RewriteEngine on
    RewriteRule ^/(.+).jsp http://tomcat_vhost:8080/$1.jsp [R]
    ....
</VirtualHost>

And i've got my Tomcat configured with virtual Hosts, so that it looks like this:

<Host name="tomcat_vhost" appbase="/home/user/www"">
    <Context path="" docbase="." />
</Host>

In my Case both tomcat_vhost and apache_vhost are the users name

what it does now is redirect a request made upon a jsp-file in apache to tomcat which translates an address like this:
[http://username/somepath/somefile.jsp](http://username/somepath/somefile.jsp) to [http://username:8080/somepath/somefile.jsp](http://username:8080/somepath/somefile.jsp)
and Tomcat responds... with an error not finding the file.

Now if someone can help me with the proper directives, so tomcat finds the file everything should be working. I have no idea, in what directory tomcat is looking with this configuration. It's not in the user-dir and not in the tomcat webapps-dir either.

Help?

---

### Post by docwex on 2005-08-28
okay i figured it out. my current <host>-config looks like this :

<Host name="tomcat_vhost" appbase="/home/user/www"">
<Context path="/" docbase="." debug="0" reloadable="true" />
</Host>

with the path attribute in the context-tag you can restrict execution on certain subfolders of the appbase.
Well i hope this helps anyone, who might be stuck with a similar problem

---

