---
title: "iced tea java plugin for firefox not working on gutsy"
date: 2007-10-19
forum: General Help
---

### Post by shadylookin on 2007-10-19
the iced tea java plugin that pops up when i opend a java applet to install java isn't working. The applet gets a gray background but nothing else happens. I have 64 bit AMD ubuntu. 

any suggestions to get java working?

---

### Post by desync0 on 2007-10-19
I have the same problem.

I tried installing the blackdown jre and manually linking it's mozilla plugin in to my firefox plugin directory and that was a no go. It would show up in about:plugins, but as soon as i loaded a page with java it instantly crashed firefox.

---

### Post by o3rat on 2007-10-19
Ya same problem, all the applets are greyed out. I get this error:

# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]

---

### Post by angryfirelord on 2007-10-19
Yup, no applet loading here. Oh well, I know that Opera 9.50 Alpha has a 64-bit port & it doesn't need a plugin for java.

---

### Post by shadylookin on 2007-10-19
so does anyone know how to get java working in 64 bit gutsy?

---

### Post by rogeriovinhal on 2007-10-20
I tried that also.

Blackdown java at first did not work. When I created a link to the plugin, it simply crashed firefox just as I tried to interact with anything with an applet.

Icedtea also shows only a gray back where the applet should be...

Isn't there anything to do to make Java work in 64 bits? I really don't want to install Firefox 32 bit, it has some serious problems with the interaction with other programs outside Firefox while running it.

---

### Post by dcstar on 2007-10-20
> **rogeriovinhal said:**
> I tried that also.

Blackdown java at first did not work. When I created a link to the plugin, it simply crashed firefox just as I tried to interact with anything with an applet.

Icedtea also shows only a gray back where the applet should be...

Isn't there anything to do to make Java work in 64 bits? I really don't want to install Firefox 32 bit, it has some serious problems with the interaction with other programs outside Firefox while running it.

Icedtea seem to work fine for me - but I had to uninstall the other Java plugins.

I have the following packages installed:

icedtea-java7-bin
icedtea-java7-jre
icedtea-java7-plugin

---

### Post by skylark on 2007-10-21
I had the same problem. I fixed it by adding the unofficial iced-tea gutsy repository to my apt sources. I did this by appending the following lines to /etc/apt/sources.list (and then doing the usual update and upgrade):

```
# iced-tea updates
deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
```

I have noticed it can a while for some plugins to start though (up to 10 seconds with my setup) but at least they seem to work.

---

### Post by FredB on 2007-10-21
Isn't icedtea an alpha quality software ?

Are they a lot of java enabled site on the web ? ;)

---

### Post by angryfirelord on 2007-10-21
> **skylark said:**
> I had the same problem. I fixed it by adding the unofficial iced-tea gutsy repository to my apt sources. I did this by appending the following lines to /etc/apt/sources.list (and then doing the usual update and upgrade):

```
# iced-tea updates
deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
```

I have noticed it can a while for some plugins to start though (up to 10 seconds with my setup) but at least they seem to work.
Whoa, it works! Thanks you very much! :KS
[QUOTE=FredB]Isn't icedtea an alpha quality software ?[/QUOTE]
At this point, yes, but it has two featues that make 1.7 more exciting over 1.6:

-It's GPL'd. No more Sun license on Java, it's now covered under GPLv3, so this means that distros like Fedora can include it on the disc.
-It has a 64-bit plugin for Firefox. Previous versions of Java (1.6 down) didn't have this, so you'd either have to go with blackdown or gcj, both of which are buggy.

---

### Post by Maestro23 on 2007-10-21
Glad I found this thread this morning.  Java was on my to-do list for today.  Now I can sit back and have another cup of java. :lolflag:

---

### Post by JEdwardP on 2007-10-21
Thank you skylark! I was having the same problem. Collectively, you folks in these forums offer great support. I've only been a serious Linux user for about two months, and haven't had many problems per se, but I've learned quite a bit just lurking here.

---

### Post by shadylookin on 2007-10-22
> **skylark said:**
> I had the same problem. I fixed it by adding the unofficial iced-tea gutsy repository to my apt sources. I did this by appending the following lines to /etc/apt/sources.list (and then doing the usual update and upgrade):

```
# iced-tea updates
deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
```

I have noticed it can a while for some plugins to start though (up to 10 seconds with my setup) but at least they seem to work.

Thank you very much

---

### Post by johnnybirdman on 2007-10-22
> **skylark said:**
> I had the same problem. I fixed it by adding the unofficial iced-tea gutsy repository to my apt sources. I did this by appending the following lines to /etc/apt/sources.list (and then doing the usual update and upgrade):

```
# iced-tea updates
deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
```



I noted the OP was running 64-bit.  Is this fix exclusive to 64-bit?  If so, can we get this post moved to the 64-bit section?

Also, thanks for the fix.  This was the first rub I ran into since installing 7.10.

John

---

### Post by johnnybirdman on 2007-10-22
Just attempted to make this fix and sorry to say that I did not have the same success as others are apparently having.  After the addition to the sources list I now get a gray screen of a different color/shade of gray. 

I do get a message at the bottom that states "Start:applet not initialized."

Anyone have any ideas on how to make this work??

Thanks in advance.

---

### Post by rogeriovinhal on 2007-10-22
Actually I get the same different gray as jhonnybirdman. But I went down to the Java test page and the applet started very poorly, but it did.

I guess the IcedTea is very, very imature.

The ones who did it and it worked, what sites did you test it with?

---

### Post by FredB on 2007-10-23
If you want a better working iced tea, use the one made by doko on his ppa :

Add this to your /etc/apt/sources.list :

```
# iced-tea updates
deb http://people.ubuntu.com/~doko/ubuntu/"  gutsy/
deb-src http://people.ubuntu.com/~doko/ubuntu/ gutsy/
```

And upgrade your iced tea version.

It works great ;)

---

### Post by rogeriovinhal on 2007-10-23
> **FredB said:**
> If you want a better working iced tea, use the one made by doko on his ppa :

Add this to your /etc/apt/sources.list :

```
# iced-tea updates
deb http://people.ubuntu.com/~doko/ubuntu/"  gutsy/
deb-src http://people.ubuntu.com/~doko/ubuntu/ gutsy/
```

And upgrade your iced tea version.

It works great ;)

Actually, that is what I did. And I think that jhonny did that too.

---

### Post by FredB on 2007-10-23
> **johnnybirdman said:**
> I noted the OP was running 64-bit.  Is this fix exclusive to 64-bit?  If so, can we get this post moved to the 64-bit section?

Also, thanks for the fix.  This was the first rub I ran into since installing 7.10.

John

No, there are also i386 deb package on doko repository.

---

### Post by forger on 2007-10-23
what's its signature for the deb packages?

FYI, that source is for developers only:
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2007-August/000331.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2007-August/000331.html)

..meaning this could break stuff in the future.

---

### Post by johnnybirdman on 2007-10-23
> **FredB said:**
> If you want a better working iced tea, use the one made by doko on his ppa :

Add this to your /etc/apt/sources.list :

```
# iced-tea updates
deb http://people.ubuntu.com/~doko/ubuntu/"  gutsy/
deb-src http://people.ubuntu.com/~doko/ubuntu/ gutsy/
```

And upgrade your iced tea version.

It works great ;)

Yes, that/this fix is what I did do also, but no go for me. 

I guess I don't know why I would want an i386 package when I'm running 64-bit,  although, my only solution at this point is to go back to a 32-bit browser anyway..??!!

---

### Post by FredB on 2007-10-23
> **forger said:**
> what's its signature for the deb packages?

FYI, that source is for developers only:
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2007-August/000331.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2007-August/000331.html)

..meaning this could break stuff in the future.

OK. But if it could help debugging this software, why not ? Linux is also a developer system ;)

---

### Post by FredB on 2007-10-23
> **johnnybirdman said:**
> Yes, that/this fix is what I did do also, but no go for me. 

I guess I don't know why I would want an i386 package when I'm running 64-bit,  although, my only solution at this point is to go back to a 32-bit browser anyway..??!!

Both i386 and AMD64 are available. So no problems here.

---

### Post by michaeldina on 2007-10-23
I have Ubuntu 7.10 (i686) and the Java did not work in 64 bit Firefox. I fixed the problem by doing two things posted earlier in this thread. 

1) I Purged all primary Java engines except the Java 7 Icedtea packages (I installed older versions trying to solve the problem). Then I made sure that all of the Java 7 Icedtea packages were actually installed (I don't know why they were not, I may have removed some by accident when I was trying to solve the problem).

Here is a list of the Java 7 Teatimer packages I have installed

Icedtea-java7-bin
Icedtea-java7-jdk     
Icedtea-java7-plugin

I also have the Icedtea-java7-source installed but I don't think its needed for the proper operation of Java.

2) After I made sure that I had no unnecessary Java packages installed I added the extra unofficial Icetea Repository's. Make sure that you use the repository(s) that are meant for the general consumption don't use the development repositories unless you are a developer of course:) That way you don't get any buggy updates that could break your system. So use these repositories: 

# iced-tea updates
deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/   

After I updated the system with the new repository's added Java was running fine in Firefox 2.0.0.8 64bit (Firefox just updated). I want to thank everybody for all the information posted in this thread as my Ubuntu system is now running with 100% awesomeness with the Java bug squashed. I hope this post is helpful to anyone with Java problems in the i686 environment  :KS 

Update: By the way you may want to comment out the repositories after you update because a more stable version may be offered in the future in the main repositories. I tested Java at this location [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) It reported that my version of JRE is not designed for general consumer use. Thats why I say to comment out the repositories after you update so when they release a general consumer version in the main repositories there won't be any sort of weird conflict. Stuff like that could get very ugly.

Cheers

Linux= Freedom
Rock n Roll= Freedom

Linux= Rock 'n Roll    Keep on Rockin!!

:guitar:

---

### Post by o3rat on 2007-10-24
@skylark

great solution, works like a charm!

---

### Post by speedwell68 on 2007-10-24
> **skylark said:**
> I had the same problem. I fixed it by adding the unofficial iced-tea gutsy repository to my apt sources. I did this by appending the following lines to /etc/apt/sources.list (and then doing the usual update and upgrade):

```
# iced-tea updates
deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
```

I have noticed it can a while for some plugins to start though (up to 10 seconds with my setup) but at least they seem to work.


Works a treat, thanks Dude.:KS

---

### Post by JulienPDX on 2007-10-25
and hwo does one "purge" all previous versions of java? 

thanks

J

---

### Post by FredB on 2007-10-25
> **JulienPDX said:**
> and hwo does one "purge" all previous versions of java? 

thanks

J

Remove it in Synaptic it is simpler than using the --purge option of apt-get / aptitude.

---

### Post by michaeldina on 2007-10-25
I said that all other versions of Java that are not Icetea should be purged (completely removed) so that there won't be any config files left over that would cause problems. I don't know if it makes a difference or not I'm not a Linux expert and I don't pretend to be but in my experience its better safe than sorry. 

Linux= Freedom 
Rock n Roll= Freedom

Linux= Rock n Roll   Keep on ROCKIN!!!

:guitar:

---

### Post by Juris on 2007-10-25
I know this is a very basic question, but how do I acquire the permissions to write to /etc/apt/sources.list? I tried the chmod command, but to no avail -- I'm without the permission to.

---

### Post by johnnybirdman on 2007-10-25
> **Juris said:**
> I know this is a very basic question, but how do I acquire the permissions to write to /etc/apt/sources.list? I tried the chmod command, but to no avail -- I'm without the permission to.

in terminal you can either do 

```
sudo nano /etc/apt/sources.list
``` (if you like command line)
or
```
sudo gedit /etc/apt/sources.list
```(if you want an easier window)

Make the changes and save.

---

### Post by Juris on 2007-10-25
Heh. So very, very simple. Sorry about that. New to this.

Yeah, it works for the most part, but for certain sites the applet fails to initialize. I get a grey(er) box than before. But I know the applet works, having tested it at [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

But many thanks to all.

---

### Post by Grellin on 2007-10-26
After removing the previous version in Synaptic and adding the repositories, it works great. Thanks!

---

### Post by smaller on 2007-10-26
Could somebody please post the version number of icedtea in the doko repositories? Because I added the doko repositories and I don't see a newer version then the one in the normal repositories.... My version currently is: 7~b21-1.4~20071007-0ubuntu6

---

### Post by smaller on 2007-10-26
Never mind! I assumed that restarting synaptic would reload the package lists from the repositories, which apparently it doesn't. A simple press on the reload button within Synaptic solved it. Version 7~b22-1.5~20071018 is now up and running.

The testapplet on the sunsite works, unfortunately the applet that I wanted to get working (home banking) is not. Back to 32 bit for me then... Does anybody know if it is possible to get the 32bit javaplugin working with firefox 64bit. Or do I have to install the 32bit version of firefox as well.

---

### Post by jenhsun on 2007-10-26
> **smaller said:**
> Never mind! I assumed that restarting synaptic would reload the package lists from the repositories, which apparently it doesn't. A simple press on the reload button within Synaptic solved it. Version 7~b22-1.5~20071018 is now up and running.

The testapplet on the sunsite works, unfortunately the applet that I wanted to get working (home banking) is not. Back to 32 bit for me then... Does anybody know if it is possible to get the 32bit javaplugin working with firefox 64bit. Or do I have to install the 32bit version of firefox as well.

Home banking?? Is that online banking or just an application?
If the test applet from sun works, that means it works.

---

### Post by johnnybirdman on 2007-10-26
> **jenhsun said:**
> Home banking?? Is that online banking or just an application?
If the test applet from sun works, that means it works.

Ya. the java test site seems to work for me as well, but my 'file manager' for webmin to admin my server is the page I really care about, and that is just shades of gray.

---

### Post by jenhsun on 2007-10-26
> **johnnybirdman said:**
> Ya. the java test site seems to work for me as well, but my 'file manager' for webmin to admin my server is the page I really care about, and that is just shades of gray.

Is that possible Sun Java != IcedTea Java ??
Do you want to try IcedTea in your server? Have some fun to do testing...
But please don't blame me crash your site.
Anyway, I would like to see your result.

---

### Post by smaller on 2007-10-26
> **jenhsun said:**
> Home banking?? Is that online banking or just an application?
If the test applet from sun works, that means it works.

I meant online banking mate... If it were just an application I wouldn't be needing icedtea now would I? 
I've already got plenty of JRE's installed, just none with a fully working plugin for firefox. And apparently now that I've got icedtea working it seems that this one's plugin isn't fully working either, but I guess at least it already has one.... :)

---

### Post by fredbeltrao on 2007-10-27
> **jenhsun said:**
> Home banking?? Is that online banking or just an application?
If the test applet from sun works, that means it works.

The test applet on Sun site also works for me. But the applet I really want to use doesn't work: 

[http://br.advfn.com/p.php?pid=desktop]("http://br.advfn.com/p.php?pid=desktop")

Does this applet work for you?

---

### Post by jenhsun on 2007-10-27
> **fredbeltrao said:**
> The test applet on Sun site also works for me. But the applet I really want to use doesn't work: 

[http://br.advfn.com/p.php?pid=desktop]("http://br.advfn.com/p.php?pid=desktop")

Does this applet work for you?

Do you mean this one?

---

### Post by nikolajsheller on 2007-10-27
I've just upgraded from 7.04 to 7.10 on a 64 bit machine.
Java test applets work, but my homebanking does not ([https://www.netbank.nordea.dk/netbank/](https://www.netbank.nordea.dk/netbank/)). 
The applet should load and ask for a password regardless. I get a gray box.

The console output is as follows:

> 
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback return
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback: setting status load: class com.ibm.cbt.thinclient.netbank.LogonApplet.class not found.
  PIPE: plugin read: status load: class com.ibm.cbt.thinclient.netbank.LogonApplet.class not found.
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback return
  PIPE: appletviewer wrote: status load: class com.ibm.cbt.thinclient.netbank.LogonApplet.class not found.
load: class com.ibm.cbt.thinclient.netbank.LogonApplet.class not found.
java.lang.ClassNotFoundException: com.ibm.cbt.thinclient.netbank.LogonApplet.class
        at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:201)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:324)
        at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:145)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:269)
        at sun.applet.AppletClassLoader.loadCode(AppletClassLoader.java:644)
        at sun.applet.AppletPanel.createApplet(AppletPanel.java:797)
        at sun.applet.AppletPanel.runLoader(AppletPanel.java:726)
        at sun.applet.AppletPanel.run(AppletPanel.java:380)
        at java.lang.Thread.run(Thread.java:675)
Caused by: java.net.SocketException: java.security.NoSuchAlgorithmException: Error constructing implementation (algorithm: Default, provider: SunJSSE, class: sun.security.ssl.DefaultSSLContextImpl)
        at javax.net.ssl.DefaultSSLSocketFactory.throwException(SSLSocketFactory.java:197)
        at javax.net.ssl.DefaultSSLSocketFactory.createSocket(SSLSocketFactory.java:217)
        at sun.net.[www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:384](www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:384))
        at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:186](www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:186))
        at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1020](www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1020))
        at java.net.HttpURLConnection.getResponseCode(HttpURLConnection.java:397)
        at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getResponseCode(HttpsURLConnectionImpl.java:339](www.protocol.https.HttpsURLConnectionImpl.getResponseCode(HttpsURLConnectionImpl.java:339))
        at sun.applet.AppletClassLoader.getBytes(AppletClassLoader.java:302)
        at sun.applet.AppletClassLoader.access$100(AppletClassLoader.java:62)
        at sun.applet.AppletClassLoader$1.run(AppletClassLoader.java:191)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:188)
        ... 8 more



Regards
-Nikolaj

---

### Post by fredbeltrao on 2007-10-27
> **jenhsun said:**
> Do you mean this one?

Unfortelly not. This screenshot is only a login screen. You must do a logon to access the applet. The register is free.

Can you register yourself and try to access the applet?

This is the English version of the site: [http://us.advfn.com/p.php?pid=mon]("http://us.advfn.com/p.php?pid=mon")

---

### Post by fredbeltrao on 2007-10-27
This is my console when I try to access the applet [http://br.advfn.com/p.php?pid=desktop]("http://br.advfn.com/p.php?pid=desktop") (free login required):

```
GCJ PLUGIN: thread 0x6195b0: NP_Initialize
GCJ PLUGIN: thread 0x6195b0: plugin_test_appletviewer
GCJ PLUGIN: thread 0x6195b0: plugin_test_appletviewer return
GCJ PLUGIN: thread 0x6195b0: NP_Initialize: using /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/../../bin/pluginappletviewer
GCJ PLUGIN: thread 0x6195b0: NP_Initialize return
GCJ PLUGIN: thread 0x6195b0: GCJ_New
GCJ PLUGIN: thread 0x6195b0: plugin_data_new
GCJ PLUGIN: thread 0x6195b0: plugin_data_new return
GCJ PLUGIN: thread 0x6195b0: plugin_get_documentbase
GCJ PLUGIN: thread 0x6195b0: plugin_get_documentbase return
GCJ PLUGIN: thread 0x6195b0: GCJ_New: creating input fifo: /home/fred/.gcjwebplugin/gcj-instance-15038-0-appletviewer-to-plugin
GCJ PLUGIN: thread 0x6195b0: GCJ_New: created input fifo: /home/fred/.gcjwebplugin/gcj-instance-15038-0-appletviewer-to-plugin
GCJ PLUGIN: thread 0x6195b0: GCJ_New: creating output fifo: /home/fred/.gcjwebplugin/gcj-instance-15038-0-plugin-to-appletviewer
GCJ PLUGIN: thread 0x6195b0: GCJ_New: created output fifo: /home/fred/.gcjwebplugin/gcj-instance-15038-0-plugin-to-appletviewer
GCJ PLUGIN: thread 0x6195b0: plugin_start_appletviewer
GCJ PLUGIN: thread 0x6195b0: plugin_start_appletviewer return
GCJ PLUGIN: thread 0x6195b0: GCJ_New: got confirmation that appletviewer is running.
  PIPE: appletviewer wrote: runningGCJ PLUGIN: thread 0x6195b0: plugin_create_applet_tag

GCJ PLUGIN: thread 0x6195b0: plugin_create_applet_tag return
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-15038-0
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: tag http://br.advfn.com/p.php?pid=desktop&java_vm=sun&fp=9.0.48 <EMBED CODE="loader3.SunLoaderApplet.class" ARCHIVE="loader.jar" CODEBASE="http://br.advfn.com/" HEIGHT="550" WIDTH="980" ><PARAM NAME="name" VALUE="Desktop"><PARAM NAME="id" VALUE="Desktop"><PARAM NAME="mayscript" VALUE=""><PARAM NAME="alt" VALUE="This browser either has java disabled or does not support it"><PARAM NAME="manifestcrc" VALUE="1323456149"><PARAM NAME="storagepath" VALUE="br.advfn.com"><PARAM NAME="masterloader" VALUE="master"><PARAM NAME="advfn_url" VALUE="http://br.advfn.com/"><PARAM NAME="streamer" VALUE="stream2.advfn.com"><PARAM NAME="user" VALUE="fredbeltrao"><PARAM NAME="root" VALUE="advfnclient.framework.BaseControl"><PARAM NAME="page" VALUE="advfnclient.desktop.Desktop"><PARAM NAME="tz" VALUE="America/Sao_Paulo"><PARAM NAME="clearAllDateStamp" VALUE="1106135848104"><PARAM NAME="clearCacheDateStamp" VALUE="1092832857604"><PARAM NAME="language" VALUE="br"><PARAM NAME="view" VALUE="br"><PARAM NAME="config_name" VALUE=""><PARAM NAME="config_default" VALUE="Default"><PARAM NAME="params" VALUE="w=980&h=550&preset=&sid=MTE5MzEwNjQ1Mi4xMXw3MDIwfDEwLjAuMS4zNQ%3D%3D&page_key=1193998397&w=980&h=550&pid=applet_embed&mypid=desktop"></EMBED>
  PIPE: appletviewer read: instance-15038-0GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: GCJ_New return

GCJ PLUGIN: thread 0x6195b0: NP_GetValue
GCJ PLUGIN: thread 0x6195b0: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x6195b0: NP_GetValue return
GCJ PLUGIN: thread 0x6195b0: GCJ_GetValue
GCJ PLUGIN: thread 0x6195b0: GCJ_GetValue: returning TRUE for NeedsXEmbed.
GCJ PLUGIN: thread 0x6195b0: GCJ_GetValue return
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow: setting window.
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-15038-0
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: handle 31461570
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow return
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow: window already exists.
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow: window width changed.
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-15038-0
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: width 980
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow: window height changed.
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-15038-0
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: height 550
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow return
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow: window already exists.
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow return
  PIPE: appletviewer read: tag http://br.advfn.com/p.php?pid=desktop&java_vm=sun&fp=9.0.48 <EMBED CODE="loader3.SunLoaderApplet.class" ARCHIVE="loader.jar" CODEBASE="http://br.advfn.com/" HEIGHT="550" WIDTH="980" ><PARAM NAME="name" VALUE="Desktop"><PARAM NAME="id" VALUE="Desktop"><PARAM NAME="mayscript" VALUE=""><PARAM NAME="alt" VALUE="This browser either has java disabled or does not support it"><PARAM NAME="manifestcrc" VALUE="1323456149"><PARAM NAME="storagepath" VALUE="br.advfn.com"><PARAM NAME="masterloader" VALUE="master"><PARAM NAME="advfn_url" VALUE="http://br.advfn.com/"><PARAM NAME="streamer" VALUE="stream2.advfn.com"><PARAM NAME="user" VALUE="fredbeltrao"><PARAM NAME="root" VALUE="advfnclient.framework.BaseControl"><PARAM NAME="page" VALUE="advfnclient.desktop.Desktop"><PARAM NAME="tz" VALUE="America/Sao_Paulo"><PARAM NAME="clearAllDateStamp" VALUE="1106135848104"><PARAM NAME="clearCacheDateStamp" VALUE="1092832857604"><PARAM NAME="language" VALUE="br"><PARAM NAME="view" VALUE="br"><PARAM NAME="config_name" VALUE=""><PARAM NAME="config_default" VALUE="Default"><PARAM NAME="params" VALUE="w=980&h=550&preset=&sid=MTE5MzEwNjQ1Mi4xMXw3MDIwfDEwLjAuMS4zNQ%3D%3D&page_key=1193998397&w=980&h=550&pid=applet_embed&mypid=desktop"></EMBED>
  PIPE: appletviewer read: instance-15038-0
  PIPE: appletviewer read: handle 31461570
Warning: <param name=... value=...> tag requires name attribute.
Warning: <param name=... value=...> tag requires name attribute.
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback: setting status starting applet...
  PIPE: appletviewer wrote: status starting applet...  PIPE: plugin read: status starting applet...
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback return

  PIPE: appletviewer read: instance-15038-0
  PIPE: appletviewer read: width 980
  PIPE: appletviewer read: instance-15038-0
  PIPE: appletviewer read: height 550
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback
  PIPE: appletviewer wrote: status Applet loaded.
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback: setting status Applet loaded.
  PIPE: plugin read: status Applet loaded.
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback return
  PIPE: appletviewer wrote: status Applet initialized.
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback: setting status Applet initialized.
  PIPE: plugin read: status Applet initialized.
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback return
  PIPE: appletviewer wrote: status Applet started.
Exception in thread "LoadControl" java.security.AccessControlException: access denied (java.lang.RuntimePermission createSecurityManager)
        at java.security.AccessControlContext.checkPermission(AccessControlContext.java:342)
        at java.security.AccessController.checkPermission(AccessController.java:556)
        at java.lang.SecurityManager.checkPermission(SecurityManager.java:550)
        at java.lang.SecurityManager.<init>(SecurityManager.java:300)
        at loader3.LocalSecurityManager.<init>(Unknown Source)
        at loader3.SunLoaderApplet.run(Unknown Source)
        at java.lang.Thread.run(Thread.java:675)
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback: setting status Applet started.
  PIPE: plugin read: status Applet started.
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback return

```

---

### Post by fredbeltrao on 2007-10-27
And this is my /usr/lib/jvm dir content:

```
fred@marte:/usr/lib/jvm$ ls -al
total 92
drwxr-xr-x   4 root root  4096 2007-10-27 08:39 .
drwxr-xr-x 179 root root 69632 2007-10-25 19:02 ..
drwxr-xr-x   5 root root  4096 2007-10-25 12:55 java-1.5.0-gcj-4.2-1.5.0.0
drwxr-xr-x   5 root root  4096 2007-10-25 19:21 java-7-icedtea
-rw-r--r--   1 root root  2709 2007-10-18 10:24 .java-7-icedtea.jinfo
lrwxrwxrwx   1 root root    26 2007-10-25 12:55 java-gcj -> java-1.5.0-gcj-4.2-1.5.0.0
-rw-r--r--   1 root root   997 2007-08-06 00:21 .java-gcj.jinfo

```

---

### Post by jenhsun on 2007-10-27
> **fredbeltrao said:**
> Unfortelly not. This screenshot is only a login screen. You must do a logon to access the applet. The register is free.

Can you register yourself and try to access the applet?

This is the English version of the site: [http://us.advfn.com/p.php?pid=mon]("http://us.advfn.com/p.php?pid=mon")

OK, I think I know what your problem is.
First of all, After I register to it, I can login, I can see the basic static applet chart.
However, I can't see dynamic chart from applet.
I think you better switch back to original sun's java JRE.
I think this's not your browser or pc fault, it's the design of this web app's fault.
Sorry for any inconvenient and stupid solution from mine. I apologies.

---

### Post by jenhsun on 2007-10-27
By the way, walk with me to solve your problem.
I will give you my solution.

---

### Post by fredbeltrao on 2007-10-27
Hi jenhshu,

Thanks for your time. If you just can see the applet, then it works for you. I think you can't see live data because today is saturday and the market is closed.

Do you use AMD64? This applet is not working for me yet. Neither that: [http://www.itautrade.com.br]("http://www.itautrade.com.br") (no logon required).

Thanks for your help.

Fred

---

### Post by fredbeltrao on 2007-10-27
> **jenhsun said:**
> OK, I think I know what your problem is.
First of all, After I register to it, I can login, I can see the basic static applet chart.
However, I can't see dynamic chart from applet.
I think you better switch back to original sun's java JRE.
I think this's not your browser or pc fault, it's the design of this web app's fault.
Sorry for any inconvenient and stupid solution from mine. I apologies.

The original sun's JRE does not support AMD64 :(

---

### Post by jenhsun on 2007-10-27
> **fredbeltrao said:**
> The original sun's JRE does not support AMD64 :(

Yes, not yet supported.
However, I think I solve your problem.
Here is what I did, you can take a look at the picture.

1. Close your firefox, make sure it's totally clean in your memory.
2. Remove everything about java from your synaptic. 
3. open your firefox, and about : plugins to check anything plugins about java. If don't, that's cool.
4. Close your firefox again. Then go to synaptic and search java, mark sun-java6-bin, it will automatic include the other dependence.
5. after install it, go to mark java-gcj-compat, java-gcj-compat-plugin, gcjwebplugin-4.1
and install these three additional.
6. open your firefox, about : plugins and check the plugins. I think you should have gcj..java.so plugin already.

The reason that I changed based on your error code which has IBM and Sun's applet class error. I think Icedtea is still under development. (actually it is Java 7, too new for it)
Anyway, you can have a try. And please report your result to everyone.

After you done these, go to this site and test.
[http://www.internetfrog.com/mypc/speedtest/](http://www.internetfrog.com/mypc/speedtest/)
Please wait the applet loading.....wait to see what happen.

---

### Post by jenhsun on 2007-10-27
More over, about using java applet for banking and trading presentation layer (means webpage) as a user.
Sometimes you will see this picture below. That means your java and the communication security in between is normal and secure. You should see this kind of message during your surf in financial and trading site.

---

### Post by jenhsun on 2007-10-27
Since you use 64 bits, try the thread for the upgrading.
[http://ubuntuforums.org/showthread.php?t=196093](http://ubuntuforums.org/showthread.php?t=196093)

If your firefox still have lockup or unstable, try this 
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

Remove your ubuntu firefox and install Mozilla's firefox by ubuntuzilla's script.

---

### Post by fredbeltrao on 2007-10-27
> **jenhsun said:**
> Yes, not yet supported.
However, I think I solve your problem.
Here is what I did, you can take a look at the picture.

1. Close your firefox, make sure it's totally clean in your memory.
2. Remove everything about java from your synaptic. 
3. open your firefox, and about : plugins to check anything plugins about java. If don't, that's cool.
4. Close your firefox again. Then go to synaptic and search java, mark sun-java6-bin, it will automatic include the other dependence.
5. after install it, go to mark java-gcj-compat, java-gcj-compat-plugin, gcjwebplugin-4.1
and install these three additional.
6. open your firefox, about : plugins and check the plugins. I think you should have gcj..java.so plugin already.

The reason that I changed based on your error code which has IBM and Sun's applet class error. I think Icedtea is still under development. (actually it is Java 7, too new for it)
Anyway, you can have a try. And please report your result to everyone.

After you done these, go to this site and test.
[http://www.internetfrog.com/mypc/speedtest/](http://www.internetfrog.com/mypc/speedtest/)
Please wait the applet loading.....wait to see what happen.

I did all the 6 steps above, and I must include the step 7:
```

fred@marte:/$ cd /home/fred/.mozilla/plugins/
fred@marte:~/.mozilla/plugins$ ln -s /usr/lib/jvm/java-gcj/jre/lib/libgcjwebplugin.so
```

"But I still haven't found what I'm looking for..." (Bono Vox) :-k

All applets are show as a grey box.

---

### Post by jenhsun on 2007-10-27
Ya, you can try.
mine is in /usr/lib/firefox/plugins
Anyway, I am testing the other way right now....

---

### Post by jenhsun on 2007-10-27
Let me give you a good news. I crash my java plugins too.
That means I already reproduce your problem in my firefox....great.....:(

---

### Post by smaller on 2007-10-27
Just wanted to let you guys know that I'm eagerly following the results of this thread as I'm still experiencing the same problem. One silly question though...I can't find where I enable the console showing the stacktrace to see if it is exactly the same problem I'm experiencing... (Probably another stacktrace but a similar problem)

---

### Post by jenhsun on 2007-10-27
OK, for my rescue reason, I try blackdown and it works. 

[http://plugindoc.mozdev.org/linux-amd64.html#java-blackdown](http://plugindoc.mozdev.org/linux-amd64.html#java-blackdown)

I forgot to do the symbolic link and mkdir plugins, That's why I totally lost.
Anyway, try the blackdown.

---

### Post by smaller on 2007-10-27
I was trying that earlier and couldn't get it working... I thought everything was configured correctly then when i opened the page in firefox it asks me to download the plugin and icedtea again. (eventhough it's already installed) Maybe I missed something???

---

### Post by smaller on 2007-10-27
By the way, you state that the packages that contain this plugin are called java-gcj-compat, java-gcj-compat-plugin, gcjwebplugin-4.1. But none of these packages are installed... And still Firefox is telling me in plugins:about that the plugin is there.

---

### Post by jenhsun on 2007-10-27
The blackdown from IBM is 100% sure to run Java plugins for firefox
[http://plugindoc.mozdev.org/linux-am...java-blackdown](http://plugindoc.mozdev.org/linux-am...java-blackdown)


However, this time I want to try the icedtea, the openjdk (Java7). Well..it works for me too.
You need to do some checking for your symbolic link, that is the tricky part.
Here are the steps:

1. Remove everything about the sun-java...or blackdown package.
2. add these to your apt sources
```
# iced-tea updates
deb http://people.ubuntu.com/~doko/ubuntu/ gutsy/
deb-src http://people.ubuntu.com/~doko/ubuntu/ gutsy/
```

3. 
```
sudo aptitude update
sudo aptitude install gcjwebplugin icedtea-java7-plugin
```

4. check your about : plugins
if nothing happened, that means you did have previous java plugin. Check your symbolic link and correct it.
```
sudo find / -iname libjavaplugin.so
```

My experience: When people upgrading or multi-install java plugin, if you don't have a) a dir folder or b) has symbolic link, the installation just avoid the plugin silently and makes user thought already done the installation, I think it suck.

Anyway, I confirm both IcedTea and Blackdown can be install in 64 bits Firefox. I hate downgrade to 32 bits firefox for just any kinds of plugin because why I have to sacrifice my 64 bits browseing power for all that...

:guitar:

---

### Post by jenhsun on 2007-10-27
> **smaller said:**
> By the way, you state that the packages that contain this plugin are called java-gcj-compat, java-gcj-compat-plugin, gcjwebplugin-4.1. But none of these packages are installed... And still Firefox is telling me in plugins:about that the plugin is there.

Sorry, these java-gcj stuff are not quite right. Please take a look at my above post.
You can also check your previous java plugin symbolic link. Maybe you will get your answer and solve the problems.

I think the 64 bits installation problem become very simple now. Since blackdown and icedtea both support 64 bits, all you have to do is doing appropriate install and check for the links.

---

### Post by jenhsun on 2007-10-27
> **nikolajsheller said:**
> I've just upgraded from 7.04 to 7.10 on a 64 bit machine.
Java test applets work, but my homebanking does not ([https://www.netbank.nordea.dk/netbank/](https://www.netbank.nordea.dk/netbank/)). 
The applet should load and ask for a password regardless. I get a gray box.

The console output is as follows:




Regards
-Nikolaj

Since your error looked like IBM's java, try blackdown.

---

### Post by smaller on 2007-10-27
Hi Jenhsun, I appreciate your time and effort on this, but your last post did not really answer my questions. (See my previous post) As for my installation:

1) I started with a clean install, nu upgrade or multi-install
2) I too refuse to go 32 bit just because of this java plugin issue
3) Blackhawk, Sun java 6, Icedtea java 7, Sun java 6 32 bit are all working on my machine standalone. (ie on the commandline java -version)
4) In firefox only Icedtea is working through the plugin. I can see the test applet, everything looks fine in about:plugins. But icedtea as you know is java 7 still under development and it seems to be having problems with some applets I REALLY need to run.
5) So I want to get another one running in firefox: sun java 6 64 bit does not have a plugin, so it's either blackdown or sun java 6 32 bit.
6) As you said blackdown is working for you, so I adapted the symbolic links to point to the blackdown plugin
7) when I restart firefox and go to the applet page it does not recognise the plugin and instead asks me to install icedtea. (This happens both when the icedteapackage is installed and when it is not, in the first case i get an error if i click on ok obviously)
8) I think this may be the case because in about:plugins i still see the gcjplugin even if icedtea is uninstalled from my system. How do I tell firefox to delete it...

Like I said mate, I really appreciate your time and effort on this. Just thought you misunderstood my situation for whatever reason?

---

### Post by smaller on 2007-10-27
Sorry for my previous post. How could I know you would do 2 more posts while I was typing up mine... :)

> **jenhsun said:**
> Sorry, these java-gcj stuff are not quite right. Please take a look at my above post..

Strange, I thought I got those packages from your post above, I'll recheck....

> **jenhsun said:**
> 
You can also check your previous java plugin symbolic link. Maybe you will get your answer and solve the problems.


I'm quite sure the links are fine, it's not hard to get right

> **jenhsun said:**
> 
I think the 64 bits installation problem become very simple now. Since blackdown and icedtea both support 64 bits, all you have to do is doing appropriate install and check for the links.

I agree, that's what I thought. But somehow I'm still getting something wrong.

---

### Post by Progressive on 2007-10-27
Same problem here. I have no idea what the problem is, but IcedTea installed yet nothing is showing up in Firefox or Konqueror. Since I refuse to use closed source java, this is a problem.

---

### Post by smaller on 2007-10-27
> **jenhsun said:**
>  You can also check your previous java plugin symbolic link. Maybe you will get your answer and solve the problems.

I solved the issue, blackdown is now working and unlike icedtea it seems to have no problem at all running my online banking applet, as I knew it would. (It did so before Gutsy)

I went back over your posts and saw that you made the symbolic link in a different place then me, under ~/mozilla/plugins. I was only updating the symbolic links under /etc/alternatives, which should normally be sufficient. (It is for icedtea at least)

It's quite annoying because this measn I will have to create this symbolic link for every user under his home dir, but at least it's working! I guess I'll just have to live with this small drawback until java-7 becomes stable enough. Again thanks for your effort, although the answer was right there in front of my nose all along.

---

### Post by fredbeltrao on 2007-10-27
Ok... I've installed Blackdown 1.4.2 from Synaptic... and I've created the proper link at my mozilla/plugins directory... about : plugins works fine... then I try the applet: [http://www.internetfrog.com/mypc/speedtest/]("http://www.internetfrog.com/mypc/speedtest/")

The result:

The applet seems to work... I could see a triangle graphic with several bandwidth benchmarks...

but...

Firefox has crash in the middle of the speed test. :(

The console only printed this:

```
fred@marte:/$ firefox
Segmentation fault (core dumped)

```

Now I will try to install icedtea again, from command line...

---

### Post by smaller on 2007-10-27
> **fredbeltrao said:**
> Ok... I've installed Blackdown 1.4.2 from Synaptic...
The applet seems to work... I could see a triangle graphic with several bandwidth benchmarks...
but...
Firefox has crash in the middle of the speed test. :(
Now I will try to install icedtea again, from command line...

fredbeltrao, as far as I can see you had first the icedtea plugin working and now the blackdown plugin too. If neither of them is able to play the applet (I just tried your applet, obviously it crashed halfway through as well) it is usueless trying to install them again but from the command line. 

As far as I can see the faults are in the plugins themselves, or god forbid, the jre's. Not much you can do about that to be honest.

---

### Post by jenhsun on 2007-10-27
> **smaller said:**
> I solved the issue, blackdown is now working and unlike icedtea it seems to have no problem at all running my online banking applet, as I knew it would. (It did so before Gutsy)

I went back over your posts and saw that you made the symbolic link in a different place then me, under ~/mozilla/plugins. I was only updating the symbolic links under /etc/alternatives, which should normally be sufficient. (It is for icedtea at least)

It's quite annoying because this measn I will have to create this symbolic link for every user under his home dir, but at least it's working! I guess I'll just have to live with this small drawback until java-7 becomes stable enough. Again thanks for your effort, although the answer was right there in front of my nose all along.

Great, good to see you solve your problems.
Sorry for previous multi-post because some info I got from this forum work fine in just several minutes. In the end I have to do hard work to trace the real problem by myself.
I am the same as you guys got problems->problem fix -> problems again -> problem fix.......looping around.

---

### Post by jenhsun on 2007-10-28
> **fredbeltrao said:**
> Ok... I've installed Blackdown 1.4.2 from Synaptic... and I've created the proper link at my mozilla/plugins directory... about : plugins works fine... then I try the applet: [http://www.internetfrog.com/mypc/speedtest/]("http://www.internetfrog.com/mypc/speedtest/")

The result:

The applet seems to work... I could see a triangle graphic with several bandwidth benchmarks...

but...

Firefox has crash in the middle of the speed test. :(

The console only printed this:

```
fred@marte:/$ firefox
Segmentation fault (core dumped)

```

Now I will try to install icedtea again, from command line...

No matter you try icedtea or blackdown, make sure your symbolic link to and from the libjavaplug.so is correct. Sometimes you can find there is /etc/alternative has your information, sometimes in your usr/lib/firefox or /usr/lib/mozilla-firefox or /usr/lib/mozilla  sometimes you might find that your libjavaplug.so is totally gone. ( I got this kind of problem before). After you can trace and solve your problem by one plugins (for example, icedtea ), then you can uninstall it and the links, and to install another plugins to see what happen. You will find that you will be very good at solve this special problems by yourself. And please remember to help others in this forum.

---

### Post by jenhsun on 2007-10-28
For fredbeltrao solution.

Because of you, I remove everything icedtea and do a blackdown version for you.

1. In you Synaptic, Remove IcedTea and any Sun related Java.
2. You should go to /etc/alternatives, /usr/lib/firefox, /usr/lib/mozilla, /usr/lib/mozilla-firefox
use ls -al to show anything related on your plugins and the symbolic link. Do you still have other javaplugin that haven't remove yet? If does, try to remove them.
3. Do a search in Synaptic for j2re1.4, you will see there are j2re1.4 and j2re1.4-mozilla-plugin these two. Install them.
4. Go to your /etc/alternatives and do   ls -al
You can take a look at pic1, there are your javaplugin so file right here.
5. Go to your /home/yourname/.mozilla/plugins, if you don't have plugins dir, try to mkdir one.
6. do a symbolic link
ln -s /etc/alternatives/libjavaplugin_oji.so /home/yourname/.mozilla/plugins/libjavaplugin_oji.so
7.Done, now your about : plugins should look like pic2.

Hope these steps by steps can solve your problems.
I hate to have automatix or ubuntuzilla like addin to fix your problem becuase you never learn from the problem you got or you might get in the future.

---

### Post by Soarer on 2007-10-28
I've been using IcedTea from the repositories for a week or so - it worked fine.

This morning, it crashes on many sites, including the Sun Java Test site. Firefox greys out & becomes unresponsive.

I have re-installed IcedTea and removed Sun 1.6 (which was still on the system) but no good. Firefox shows it has the IcedTea plugin OK.

Anything I have done to cause this?

---

### Post by jenhsun on 2007-10-28
> **Soarer said:**
> I've been using IcedTea from the repositories for a week or so - it worked fine.

This morning, it crashes on many sites, including the Sun Java Test site. Firefox greys out & becomes unresponsive.

I have re-installed IcedTea and removed Sun 1.6 (which was still on the system) but no good. Firefox shows it has the IcedTea plugin OK.

Anything I have done to cause this?

Make sure you only have one plugins at a time. Check your symbolic link.
Check your firefox version, 32 or 64 bits, 2.0.0.8 ??
What did you do for your firefox recently?

---

### Post by Soarer on 2007-10-28
> **jenhsun said:**
> Make sure you only have one plugins at a time. Check your symbolic link.
Check your firefox version, 32 or 64 bits, 2.0.0.8 ??
What did you do for your firefox recently?

Hi,

Firefox is 2.0.0.8 64bit
Symbolic link in /etc/alternatives:
firefox-javaplugin.so -> /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so

About: Plugins says: GCJ Web Browser Plugin (using IcedTea) 1.4

Really strangely, the Sun Java Test page ([http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)) crashed my FF, I just restarted FF and found - that page now works! It reports as 1.7, so it's IcedTea OK.

I had restarted before, and also re-installed Sun-Java6 from the repos, which I had un-installed.

Still, alls well that ends well - thanks for the prompt help.  :)

---

### Post by fredbeltrao on 2007-10-28
> **jenhsun said:**
> For fredbeltrao solution.

Because of you, I remove everything icedtea and do a blackdown version for you.

1. In you Synaptic, Remove IcedTea and any Sun related Java.
2. You should go to /etc/alternatives, /usr/lib/firefox, /usr/lib/mozilla, /usr/lib/mozilla-firefox
use ls -al to show anything related on your plugins and the symbolic link. Do you still have other javaplugin that haven't remove yet? If does, try to remove them.
3. Do a search in Synaptic for j2re1.4, you will see there are j2re1.4 and j2re1.4-mozilla-plugin these two. Install them.
4. Go to your /etc/alternatives and do   ls -al
You can take a look at pic1, there are your javaplugin so file right here.
5. Go to your /home/yourname/.mozilla/plugins, if you don't have plugins dir, try to mkdir one.
6. do a symbolic link
ln -s /etc/alternatives/libjavaplugin_oji.so /home/yourname/.mozilla/plugins/libjavaplugin_oji.so
7.Done, now your about : plugins should look like pic2.

Hope these steps by steps can solve your problems.
I hate to have automatix or ubuntuzilla like addin to fix your problem becuase you never learn from the problem you got or you might get in the future.

I followed these steps:
(IcedTea and Sun jvm were already not installed.)
1. Remove all old links related to javaplugin from  /etc/alternatives, /usr/lib/firefox, /usr/lib/firefox/plugins, /usr/lib/mozilla, /usr/lib/mozilla/plugins, /usr/lib/mozilla-firefox and /usr/lib/mozilla-firefox/plugins (in fact there was several links of other java plugins)
2. Reinstall  j2re1.4 and install j2re1.4-mozilla-plugin
3. Create the link:  
```
cd /home/fred/.mozilla/plugins/
ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so

```
4. about : plugins
Java(TM) Plug-in Blackdown-1.4.2-02
    Nome do arquivo: libjavaplugin_oji.so
    Blackdown Java-Linux Java(TM) Plug-in 1.4.2
...
5. Try this applet: [http://br.advfn.com/p.php?pid=charts](http://br.advfn.com/p.php?pid=charts)
Use some code to chart like GOOG
6. The applet works for about 5 seconds and firefox crash with this log:
```

Unexpected Signal : 11 occurred at PC=0x2B827778ADAA
Function=(null)+0x7778ADAA
Library=/usr/lib/j2se/1.4/jre/lib/amd64/server/libjvm.so

NOTE: We are unable to locate the function name symbol for the error
      just occurred. Please refer to release documentation for possible
      reason and solutions.


Current Java thread:
        at sun.plugin.navig.motif.AThread.handleRequest(Native Method)
        at sun.plugin.navig.motif.AThread.JNIHandleLoop(AThread.java:35)
        at sun.plugin.navig.motif.AThread.run(AThread.java:27)

Dynamic libraries:
40000000-40003000 r-xp 00000000 08:08 3140445                            /usr/lib/j2se/1.4/jre/bin/java_vm
40102000-40103000 rwxp 00002000 08:08 3140445                            /usr/lib/j2se/1.4/jre/bin/java_vm
40103000-4018f000 rwxp 40103000 00:00 0                                  [heap]
2aaaaaaac000-2aaaaaaeb000 r-xp 00000000 08:08 3074411                    /usr/lib/locale/pt_BR.utf8/LC_CTYPE
2aaaaaaeb000-2aaaaaaf2000 r-xs 00000000 08:08 3646738                    /usr/lib/gconv/gconv-modules.cache
2aaaaaaf2000-2aaaaabf2000 rwxp 2aaaaaaf2000 00:00 0 
2aaaaabf2000-2aaaaac00000 r-xs 00000000 08:08 3140862                    /usr/lib/j2se/1.4/jre/lib/ext/ldapsec.jar
2aaaaac00000-2aaaaac03000 r-xs 00000000 08:08 3140860                    /usr/lib/j2se/1.4/jre/lib/ext/dnsns.jar
2aaaaac03000-2aaaaac1f000 r-xs 00000000 08:08 3140861                    /usr/lib/j2se/1.4/jre/lib/ext/sunjce_provider.jar
2aaaaac1f000-2aaaaacdb000 r-xs 00000000 08:08 3140863                    /usr/lib/j2se/1.4/jre/lib/ext/localedata.jar
2aaaaacdb000-2aaaaadbe000 r-xp 00000000 08:08 3140893                    /usr/lib/j2se/1.4/jre/lib/amd64/libawt.so
2aaaaadbe000-2aaaaaebf000 ---p 000e3000 08:08 3140893                    /usr/lib/j2se/1.4/jre/lib/amd64/libawt.so
2aaaaaebf000-2aaaaaee0000 rwxp 000e4000 08:08 3140893                    /usr/lib/j2se/1.4/jre/lib/amd64/libawt.so
2aaaaaee0000-2aaaaaf05000 rwxp 2aaaaaee0000 00:00 0 
2aaaaaf05000-2aaaaaf5d000 r-xp 00000000 08:08 3140880                    /usr/lib/j2se/1.4/jre/lib/amd64/libmlib_image.so
2aaaaaf5d000-2aaaab05d000 ---p 00058000 08:08 3140880                    /usr/lib/j2se/1.4/jre/lib/amd64/libmlib_image.so
2aaaab05d000-2aaaab060000 rwxp 00058000 08:08 3140880                    /usr/lib/j2se/1.4/jre/lib/amd64/libmlib_image.so
2aaaab060000-2aaaab2a5000 r-xp 00000000 08:08 3140864                    /usr/lib/j2se/1.4/jre/lib/amd64/libXm.so.3
2aaaab2a5000-2aaaab3a4000 ---p 00245000 08:08 3140864                    /usr/lib/j2se/1.4/jre/lib/amd64/libXm.so.3
2aaaab3a4000-2aaaab40e000 rwxp 00244000 08:08 3140864                    /usr/lib/j2se/1.4/jre/lib/amd64/libXm.so.3
2aaaab40e000-2aaaab40f000 rwxp 2aaaab40e000 00:00 0 
2aaaab423000-2aaaab42b000 r-xp 00000000 08:08 3025333                    /usr/lib/libXp.so.6.2.0
2aaaab42b000-2aaaab62b000 ---p 00008000 08:08 3025333                    /usr/lib/libXp.so.6.2.0
2aaaab62b000-2aaaab62c000 rwxp 00008000 08:08 3025333                    /usr/lib/libXp.so.6.2.0
2aaaab62c000-2aaaab689000 r-xp 00000000 08:08 3025334                    /usr/lib/libXt.so.6.0.0
2aaaab689000-2aaaab889000 ---p 0005d000 08:08 3025334                    /usr/lib/libXt.so.6.0.0
2aaaab889000-2aaaab88f000 rwxp 0005d000 08:08 3025334                    /usr/lib/libXt.so.6.0.0
2aaaab88f000-2aaaab890000 rwxp 2aaaab88f000 00:00 0 
2aaaab890000-2aaaab898000 r-xp 00000000 08:08 3026423                    /usr/lib/libSM.so.6.0.0
2aaaab898000-2aaaaba97000 ---p 00008000 08:08 3026423                    /usr/lib/libSM.so.6.0.0
2aaaaba97000-2aaaaba98000 rwxp 00007000 08:08 3026423                    /usr/lib/libSM.so.6.0.0
2aaaaba98000-2aaaabaaf000 r-xp 00000000 08:08 3025295                    /usr/lib/libICE.so.6.3.0
2aaaabaaf000-2aaaabcaf000 ---p 00017000 08:08 3025295                    /usr/lib/libICE.so.6.3.0
2aaaabcaf000-2aaaabcb0000 rwxp 00017000 08:08 3025295                    /usr/lib/libICE.so.6.3.0
2aaaabcb0000-2aaaabcb4000 rwxp 2aaaabcb0000 00:00 0 
2aaaabcb4000-2aaaabcc5000 r-xp 00000000 08:08 3026458                    /usr/lib/libXext.so.6.4.0
2aaaabcc5000-2aaaabec4000 ---p 00011000 08:08 3026458                    /usr/lib/libXext.so.6.4.0
2aaaabec4000-2aaaabec5000 rwxp 00010000 08:08 3026458                    /usr/lib/libXext.so.6.4.0
2aaaabec5000-2aaaabeca000 r-xp 00000000 08:08 3025330                    /usr/lib/libXtst.so.6.1.0
2aaaabeca000-2aaaac0ca000 ---p 00005000 08:08 3025330                    /usr/lib/libXtst.so.6.1.0
2aaaac0ca000-2aaaac0cb000 rwxp 00005000 08:08 3025330                    /usr/lib/libXtst.so.6.1.0
2aaaac0cb000-2aaaac1d5000 r-xp 00000000 08:08 3026421                    /usr/lib/libX11.so.6.2.0
2aaaac1d5000-2aaaac3d5000 ---p 0010a000 08:08 3026421                    /usr/lib/libX11.so.6.2.0
2aaaac3d5000-2aaaac3dc000 rwxp 0010a000 08:08 3026421                    /usr/lib/libX11.so.6.2.0
2aaaac3dc000-2aaaac3de000 r-xp 00000000 08:08 3025882                    /usr/lib/libXau.so.6.0.0
2aaaac3de000-2aaaac5dd000 ---p 00002000 08:08 3025882                    /usr/lib/libXau.so.6.0.0
2aaaac5dd000-2aaaac5de000 rwxp 00001000 08:08 3025882                    /usr/lib/libXau.so.6.0.0
2aaaac5de000-2aaaac5e3000 r-xp 00000000 08:08 3026415                    /usr/lib/libXdmcp.so.6.0.0
2aaaac5e3000-2aaaac7e2000 ---p 00005000 08:08 3026415                    /usr/lib/libXdmcp.so.6.0.0
2aaaac7e2000-2aaaac7e3000 rwxp 00004000 08:08 3026415                    /usr/lib/libXdmcp.so.6.0.0
2aaaac7e3000-2aaaac7f4000 r-xp 00000000 08:08 3140892                    /usr/lib/j2se/1.4/jre/lib/amd64/libjavaplugin_jni.so
2aaaac7f4000-2aaaac8f3000 ---p 00011000 08:08 3140892                    /usr/lib/j2se/1.4/jre/lib/amd64/libjavaplugin_jni.so
2aaaac8f3000-2aaaac8f6000 rwxp 00010000 08:08 3140892                    /usr/lib/j2se/1.4/jre/lib/amd64/libjavaplugin_jni.so
2aaaac8f6000-2aaaac91e000 rwxp 2aaaac8f6000 00:00 0 
2aaaac91e000-2aaaac9bb000 r-xp 00000000 08:08 3140874                    /usr/lib/j2se/1.4/jre/lib/amd64/libfontmanager.so
2aaaac9bb000-2aaaacaba000 ---p 0009d000 08:08 3140874                    /usr/lib/j2se/1.4/jre/lib/amd64/libfontmanager.so
2aaaacaba000-2aaaacad9000 rwxp 0009c000 08:08 3140874                    /usr/lib/j2se/1.4/jre/lib/amd64/libfontmanager.so
2aaaacad9000-2aaaacaea000 rwxp 2aaaacad9000 00:00 0 
2aaaacb1b000-2aaaacd1b000 rwxp 2aaaacb1b000 00:00 0 
2aaaacd2f000-2aaaacd39000 r-xp 00000000 08:08 3026497                    /usr/lib/libXcursor.so.1.0.2
2aaaacd39000-2aaaacf38000 ---p 0000a000 08:08 3026497                    /usr/lib/libXcursor.so.1.0.2
2aaaacf38000-2aaaacf39000 rwxp 00009000 08:08 3026497                    /usr/lib/libXcursor.so.1.0.2
2aaaacf39000-2aaaacf42000 r-xp 00000000 08:08 3058460                    /usr/lib/libXrender.so.1.3.0
2aaaacf42000-2aaaad141000 ---p 00009000 08:08 3058460                    /usr/lib/libXrender.so.1.3.0
2aaaad141000-2aaaad142000 rwxp 00008000 08:08 3058460                    /usr/lib/libXrender.so.1.3.0
2aaaad142000-2aaaad147000 r-xp 00000000 08:08 3026454                    /usr/lib/libXfixes.so.3.1.0
2aaaad147000-2aaaad346000 ---p 00005000 08:08 3026454                    /usr/lib/libXfixes.so.3.1.0
2aaaad346000-2aaaad347000 rwxp 00004000 08:08 3026454                    /usr/lib/libXfixes.so.3.1.0
2aaaad3ec000-2aaaad4ec000 rwxp 2aaaad3ec000 00:00 0 
2aaaad4ec000-2aaaad4f3000 r-xs 00000000 08:07 473833                     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2aaaad4f3000-2aaaad4f8000 r-xs 00000000 08:07 473798                     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2aaaad4f8000-2aaaad4fe000 r-xs 00000000 08:07 473837                     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86-64.cache-2
2aaaad4fe000-2aaaad509000 r-xs 00000000 08:07 473835                     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86-64.cache-2
2aaaad509000-2aaaad50a000 r-xs 00000000 08:07 473838                     /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86-64.cache-2
2aaaad50a000-2aaaad512000 r-xs 00000000 08:07 473805                     /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86-64.cache-2
2aaaad512000-2aaaad519000 r-xs 00000000 08:07 473839                     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86-64.cache-2
2aaaad519000-2aaaad51b000 r-xs 00000000 08:07 472500                     /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86-64.cache-2
2aaaad51b000-2aaaad51c000 r-xs 00000000 08:07 472526                     /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86-64.cache-2
2aaaad51c000-2aaaad51d000 r-xs 00000000 08:07 473807                     /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86-64.cache-2
2aaaad51d000-2aaaad521000 r-xs 00000000 08:07 472499                     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86-64.cache-2
2aaaad521000-2aaaad524000 r-xs 00000000 08:07 472529                     /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86-64.cache-2
2aaaad524000-2aaaad52a000 r-xs 00000000 08:07 473802                     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86-64.cache-2
2aaaad52a000-2aaaad531000 r-xs 00000000 08:07 472530                     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86-64.cache-2
2aaaad531000-2aaaad532000 r-xs 00000000 08:07 472531                     /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86-64.cache-2
2aaaad532000-2aaaad535000 r-xs 00000000 08:07 473800                     /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86-64.cache-2
2aaaad535000-2aaaad536000 r-xs 00000000 08:07 472438                     /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86-64.cache-2
2aaaad536000-2aaaad539000 r-xs 00000000 08:07 472504                     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86-64.cache-2
2aaaad539000-2aaaad544000 r-xs 00000000 08:07 473794                     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86-64.cache-2
2aaaad544000-2aaaad548000 r-xs 00000000 08:07 473806                     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86-64.cache-2
2aaaad548000-2aaaad54b000 r-xs 00000000 08:07 473796                     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86-64.cache-2
2aaaad54b000-2aaaad54c000 r-xs 00000000 08:07 473808                     /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86-64.cache-2
2aaaad54c000-2aaaad54d000 r-xs 00000000 08:07 473809                     /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86-64.cache-2
2aaaad54d000-2aaaad54e000 r-xs 00000000 08:07 473811                     /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86-64.cache-2
2aaaad54e000-2aaaad54f000 r-xs 00000000 08:07 473799                     /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86-64.cache-2
2aaaad54f000-2aaaad559000 r-xs 00000000 08:07 473836                     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86-64.cache-2
2aaaad559000-2aaaad55e000 r-xs 00000000 08:07 472727                     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
2aaaad55e000-2aaaad562000 r-xs 00000000 08:07 473793                     /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86-64.cache-2
2aaaad562000-2aaaad569000 r-xs 00000000 08:07 472571                     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
2aaaad569000-2aaaad56c000 r-xs 00000000 08:07 472563                     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
2aaaad56c000-2aaaad58b000 r-xs 00000000 08:07 472502                     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86-64.cache-2
2aaaad58b000-2aaaad58c000 r-xs 00000000 08:07 472501                     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
2aaaad58c000-2aaaad594000 r-xs 00000000 08:07 473810                     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
2aaaad594000-2aaaad59f000 r-xs 00000000 08:07 473812                     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
2aaaad59f000-2aaaad5a1000 r-xs 00000000 08:07 473813                     /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86-64.cache-2
2aaaad5a1000-2aaaad5a4000 r-xs 00000000 08:07 473814                     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
2aaaad5a4000-2aaaad5ac000 r-xs 00000000 08:07 473815                     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
2aaaad5ac000-2aaaad5af000 r-xs 00000000 08:07 473816                     /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86-64.cache-2
2aaaad5af000-2aaaad5b1000 r-xs 00000000 08:07 473817                     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86-64.cache-2
2aaaad5b1000-2aaaad5b3000 r-xs 00000000 08:07 473818                     /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86-64.cache-2
2aaaad5b3000-2aaaad5b7000 r-xs 00000000 08:07 473819                     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
2aaaad5b7000-2aaaad5b9000 r-xs 00000000 08:07 473820                     /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86-64.cache-2
2aaaad5b9000-2aaaad5ba000 r-xs 00000000 08:07 473821                     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
2aaaad5ba000-2aaaad5bb000 r-xs 00000000 08:07 473822                     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86-64.cache-2
2aaaad5bb000-2aaaad5c0000 r-xs 00000000 08:07 473823                     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86-64.cache-2
2aaaad5c0000-2aaaad5c1000 r-xs 00000000 08:07 473824                     /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86-64.cache-2
2aaaad5c1000-2aaaad5c2000 r-xs 00000000 08:07 473825                     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86-64.cache-2
2aaaad5c2000-2aaaad5c5000 r-xs 00000000 08:07 473826                     /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86-64.cache-2
2aaaad5c5000-2aaaad5c6000 r-xs 00000000 08:07 473827                     /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86-64.cache-2
2aaaad5c6000-2aaaad5c9000 r-xs 00000000 08:07 473828                     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86-64.cache-2
2aaaad5c9000-2aaaad5d1000 r-xs 00000000 08:07 473830                     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
2aaaad5d1000-2aaaad8d1000 rwxp 2aaaad5d1000 00:00 0 
2aaaad8d1000-2aaaad8df000 r-xp 00000000 08:08 3140865                    /usr/lib/j2se/1.4/jre/lib/amd64/libnet.so
2aaaad8df000-2aaaad9de000 ---p 0000e000 08:08 3140865                    /usr/lib/j2se/1.4/jre/lib/amd64/libnet.so
2aaaad9de000-2aaaad9e1000 rwxp 0000d000 08:08 3140865                    /usr/lib/j2se/1.4/jre/lib/amd64/libnet.so
2aaaad9e2000-2aaaad9fb000 r-xp 00000000 08:08 3140887                    /usr/lib/j2se/1.4/jre/lib/amd64/libdcpr.so
2aaaad9fb000-2aaaadafa000 ---p 00019000 08:08 3140887                    /usr/lib/j2se/1.4/jre/lib/amd64/libdcpr.so
2aaaadafa000-2aaaadb11000 rwxp 00018000 08:08 3140887                    /usr/lib/j2se/1.4/jre/lib/amd64/libdcpr.so
2aaaadb25000-2aaaadb27000 r-xp 00000000 08:05 127663                     /lib/libnss_mdns4_minimal.so.2
2aaaadb27000-2aaaadd26000 ---p 00002000 08:05 127663                     /lib/libnss_mdns4_minimal.so.2
2aaaadd26000-2aaaadd27000 rwxp 00001000 08:05 127663                     /lib/libnss_mdns4_minimal.so.2
2aaaadd27000-2aaaadd2b000 r-xp 00000000 08:05 127812                     /lib/libnss_dns-2.6.1.so
2aaaadd2b000-2aaaadf2b000 ---p 00004000 08:05 127812                     /lib/libnss_dns-2.6.1.so
2aaaadf2b000-2aaaadf2d000 rwxp 00004000 08:05 127812                     /lib/libnss_dns-2.6.1.so
2aaaadf2d000-2aaaadf3f000 r-xp 00000000 08:05 127819                     /lib/libresolv-2.6.1.so
2aaaadf3f000-2aaaae13e000 ---p 00012000 08:05 127819                     /lib/libresolv-2.6.1.so
2aaaae13e000-2aaaae140000 rwxp 00011000 08:05 127819                     /lib/libresolv-2.6.1.so
2aaaae140000-2aaaaea71000 rwxp 2aaaae140000 00:00 0 
2aaaaea71000-2aaaaea77000 r-xs 00000000 08:06 16                         /tmp/jar_cache11871.tmp (deleted)
2aaaaea77000-2aaaaea78000 rwxp 2aaaaea77000 00:00 0 
2aaab0000000-2aaab0b9a000 rwxp 2aaab0000000 00:00 0 
2aaab0b9a000-2aaab4000000 ---p 2aaab0b9a000 00:00 0 
2b8276ac0000-2b8276add000 r-xp 00000000 08:05 127492                     /lib/ld-2.6.1.so
2b8276add000-2b8276ae0000 rwxp 2b8276add000 00:00 0 
2b8276cdc000-2b8276cde000 rwxp 0001c000 08:05 127492                     /lib/ld-2.6.1.so
2b8276cde000-2b8276cf4000 r-xp 00000000 08:05 127818                     /lib/libpthread-2.6.1.so
2b8276cf4000-2b8276ef3000 ---p 00016000 08:05 127818                     /lib/libpthread-2.6.1.so
2b8276ef3000-2b8276ef5000 rwxp 00015000 08:05 127818                     /lib/libpthread-2.6.1.so
2b8276ef5000-2b8276ef9000 rwxp 2b8276ef5000 00:00 0 
2b8276ef9000-2b8276efb000 r-xp 00000000 08:05 127807                     /lib/libdl-2.6.1.so
2b8276efb000-2b82770fb000 ---p 00002000 08:05 127807                     /lib/libdl-2.6.1.so
2b82770fb000-2b82770fd000 rwxp 00002000 08:05 127807                     /lib/libdl-2.6.1.so
2b82770fd000-2b827724f000 r-xp 00000000 08:05 127804                     /lib/libc-2.6.1.so
2b827724f000-2b827744e000 ---p 00152000 08:05 127804                     /lib/libc-2.6.1.so
2b827744e000-2b8277451000 r-xp 00151000 08:05 127804                     /lib/libc-2.6.1.so
2b8277451000-2b8277453000 rwxp 00154000 08:05 127804                     /lib/libc-2.6.1.so
2b8277453000-2b827745a000 rwxp 2b8277453000 00:00 0 
2b827745a000-2b8277999000 r-xp 00000000 08:08 3189009                    /usr/lib/j2se/1.4/jre/lib/amd64/server/libjvm.so
2b8277999000-2b8277a9a000 ---p 0053f000 08:08 3189009                    /usr/lib/j2se/1.4/jre/lib/amd64/server/libjvm.so
2b8277a9a000-2b8277bc6000 rwxp 00540000 08:08 3189009                    /usr/lib/j2se/1.4/jre/lib/amd64/server/libjvm.so
2b8277bc6000-2b8277bf8000 rwxp 2b8277bc6000 00:00 0 
2b8277c0c000-2b8277c22000 r-xp 00000000 08:05 127810                     /lib/libnsl-2.6.1.so
2b8277c22000-2b8277e21000 ---p 00016000 08:05 127810                     /lib/libnsl-2.6.1.so
2b8277e21000-2b8277e23000 rwxp 00015000 08:05 127810                     /lib/libnsl-2.6.1.so
2b8277e23000-2b8277e25000 rwxp 2b8277e23000 00:00 0 
2b8277e25000-2b8277ea5000 r-xp 00000000 08:05 127808                     /lib/libm-2.6.1.so
2b8277ea5000-2b82780a4000 ---p 00080000 08:05 127808                     /lib/libm-2.6.1.so
2b82780a4000-2b82780a6000 rwxp 0007f000 08:05 127808                     /lib/libm-2.6.1.so
2b82780a6000-2b82780ae000 r-xp 00000000 08:08 3140877                    /usr/lib/j2se/1.4/jre/lib/amd64/native_threads/libhpi.so
2b82780ae000-2b82781ae000 ---p 00008000 08:08 3140877                    /usr/lib/j2se/1.4/jre/lib/amd64/native_threads/libhpi.so
2b82781ae000-2b82781b0000 rwxp 00008000 08:08 3140877                    /usr/lib/j2se/1.4/jre/lib/amd64/native_threads/libhpi.so
2b82781b0000-2b82781b1000 rwxp 2b82781b0000 00:00 0 
2b82781b1000-2b82781b5000 rwxs 00000000 08:06 45988                      /tmp/hsperfdata_fred/7461
2b82781c5000-2b82781cd000 r-xp 00000000 08:05 127811                     /lib/libnss_compat-2.6.1.so
2b82781cd000-2b82783cc000 ---p 00008000 08:05 127811                     /lib/libnss_compat-2.6.1.so
2b82783cc000-2b82783ce000 rwxp 00007000 08:05 127811                     /lib/libnss_compat-2.6.1.so
2b82783ce000-2b82783d8000 r-xp 00000000 08:05 127815                     /lib/libnss_nis-2.6.1.so
2b82783d8000-2b82785d7000 ---p 0000a000 08:05 127815                     /lib/libnss_nis-2.6.1.so
2b82785d7000-2b82785d9000 rwxp 00009000 08:05 127815                     /lib/libnss_nis-2.6.1.so
2b82785d9000-2b82785e3000 r-xp 00000000 08:05 127813                     /lib/libnss_files-2.6.1.so
2b82785e3000-2b82787e2000 ---p 0000a000 08:05 127813                     /lib/libnss_files-2.6.1.so
2b82787e2000-2b82787e4000 rwxp 00009000 08:05 127813                     /lib/libnss_files-2.6.1.so
2b82787e4000-2b82787f6000 r-xp 00000000 08:08 3140869                    /usr/lib/j2se/1.4/jre/lib/amd64/libverify.so
2b82787f6000-2b82788f5000 ---p 00012000 08:08 3140869                    /usr/lib/j2se/1.4/jre/lib/amd64/libverify.so
2b82788f5000-2b82788f8000 rwxp 00011000 08:08 3140869                    /usr/lib/j2se/1.4/jre/lib/amd64/libverify.so
2b82788f8000-2b8278918000 r-xp 00000000 08:08 3140882                    /usr/lib/j2se/1.4/jre/lib/amd64/libjava.so
2b8278918000-2b8278a18000 ---p 00020000 08:08 3140882                    /usr/lib/j2se/1.4/jre/lib/amd64/libjava.so
2b8278a18000-2b8278a1d000 rwxp 00020000 08:08 3140882                    /usr/lib/j2se/1.4/jre/lib/amd64/libjava.so
2b8278a1d000-2b8278a2e000 r-xp 00000000 08:08 3140876                    /usr/lib/j2se/1.4/jre/lib/amd64/libzip.so
2b8278a2e000-2b8278b2d000 ---p 00011000 08:08 3140876                    /usr/lib/j2se/1.4/jre/lib/amd64/libzip.so
2b8278b2d000-2b8278b31000 rwxp 00010000 08:08 3140876                    /usr/lib/j2se/1.4/jre/lib/amd64/libzip.so
2b8278b31000-2b827a4dd000 r-xs 00000000 08:08 3140902                    /usr/lib/j2se/1.4/jre/lib/rt.jar
2b827a4dd000-2b827a527000 rwxp 2b827a4dd000 00:00 0 
2b827a527000-2b827a53d000 r-xs 00000000 08:08 3140898                    /usr/lib/j2se/1.4/jre/lib/sunrsasign.jar
2b827a53d000-2b827a61a000 r-xs 00000000 08:08 3140895                    /usr/lib/j2se/1.4/jre/lib/jsse.jar
2b827a61a000-2b827a62b000 r-xs 00000000 08:08 3140900                    /usr/lib/j2se/1.4/jre/lib/jce.jar
2b827a62b000-2b827abcb000 r-xs 00000000 08:08 3140896                    /usr/lib/j2se/1.4/jre/lib/charsets.jar
2b827abcb000-2b827adad000 r-xs 00000000 08:08 3140897                    /usr/lib/j2se/1.4/jre/lib/plugin.jar
2b827adad000-2b827aead000 rwxp 2b827adad000 00:00 0 
2b827aead000-2b82badad000 rwxp 2b827aead000 00:00 0 
2b82badad000-2b82badb1000 rwxp 2b82badad000 00:00 0 
2b82badb1000-2b82bbdad000 rwxp 2b82badb1000 00:00 0 
2b82bbdad000-2b82bbdfc000 rwxp 2b82bbdad000 00:00 0 
2b82bbe00000-2b82bc360000 rwxp 2b82bbe00000 00:00 0 
2b82bc360000-2b82bd350000 rwxp 2b82bc360000 00:00 0 
2b82bd350000-2b82bddea000 rwxp 2b82bd350000 00:00 0 
2b82bddea000-2b82bfe00000 rwxp 2b82bddea000 00:00 0 
2b82bfe00000-2b82c0e00000 rwxp 2b82bfe00000 00:00 0 
2b82c0e00000-2b82c3e00000 rwxp 2b82c0e00000 00:00 0 
2b82c3e00000-2b82c3e03000 rwxp 2b82c3e00000 00:00 0 
2b82c3e03000-2b82c3e0a000 rwxp 2b82c3e03000 00:00 0 
2b82c3e0a000-2b82c3e10000 rwxp 2b82c3e0a000 00:00 0 
2b82c3e10000-2b82c3e20000 rwxp 2b82c3e10000 00:00 0 
2b82c3e20000-2b82c3e28000 rwxp 2b82c3e20000 00:00 0 
2b82c3e28000-2b82c3e40000 rwxp 2b82c3e28000 00:00 0 
2b82c3e40000-2b82c3e47000 rwxp 2b82c3e40000 00:00 0 
2b82c3e47000-2b82c3e57000 rwxp 2b82c3e47000 00:00 0 
2b82c3e57000-2b82c3e60000 rwxp 2b82c3e57000 00:00 0 
2b82c3e60000-2b82c3e78000 rwxp 2b82c3e60000 00:00 0 
7fff33dea000-7fff33dec000 rwxp 7fff33dea000 00:00 0 
7fff33dec000-7fff33def000 ---p 7fff33dec000 00:00 0 
7fff33fc5000-7fff33fea000 rwxp 7fff33fc5000 00:00 0                      [stack]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]

Heap at VM Abort:
Heap
 def new generation   total 4992K, used 16K [0x00002b82bbe00000, 0x00002b82bc360000, 0x00002b82bd350000)
  eden space 4480K,   0% used [0x00002b82bbe00000, 0x00002b82bbe042a8, 0x00002b82bc260000)
  from space 512K,   0% used [0x00002b82bc260000, 0x00002b82bc260000, 0x00002b82bc2e0000)
  to   space 512K,   0% used [0x00002b82bc2e0000, 0x00002b82bc2e0000, 0x00002b82bc360000)
 tenured generation   total 10856K, used 4211K [0x00002b82bd350000, 0x00002b82bddea000, 0x00002b82bfe00000)
   the space 10856K,  38% used [0x00002b82bd350000, 0x00002b82bd76cc38, 0x00002b82bd76ce00, 0x00002b82bddea000)
 compacting perm gen  total 16384K, used 11427K [0x00002b82bfe00000, 0x00002b82c0e00000, 0x00002b82c3e00000)
   the space 16384K,  69% used [0x00002b82bfe00000, 0x00002b82c0928c38, 0x00002b82c0928e00, 0x00002b82c0e00000)

Local Time = Sun Oct 28 09:08:08 2007
Elapsed Time = 110
#
# HotSpot Virtual Machine Error : 11
# Error ID : 4F530E43505002EF
# Please report this error at
# http://www.blackdown.org/cgi-bin/jdk
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (Blackdown-1.4.2-02 mixed mode)
#
# An error report file has been saved as hs_err_pid7461.log.
# Please refer to the file for further information.
#
Plugin: unexpected work request from child
INTERNAL ERROR on Browser End: Code = aa2a0000
System error?:: Sucesso
```

Now I will try these steps with IcedTea.

---

### Post by jenhsun on 2007-10-28
> **fredbeltrao said:**
> I followed these steps:
(IcedTea and Sun jvm were already not installed.)
1. Remove all old links related to javaplugin from  /etc/alternatives, /usr/lib/firefox, /usr/lib/firefox/plugins, /usr/lib/mozilla, /usr/lib/mozilla/plugins, /usr/lib/mozilla-firefox and /usr/lib/mozilla-firefox/plugins (in fact there was several links of other java plugins)
2. Reinstall  j2re1.4 and install j2re1.4-mozilla-plugin
3. Create the link:  
```
cd /home/fred/.mozilla/plugins/
ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so

```
4. about : plugins
Java(TM) Plug-in Blackdown-1.4.2-02
    Nome do arquivo: libjavaplugin_oji.so
    Blackdown Java-Linux Java(TM) Plug-in 1.4.2
...
5. Try this applet: [http://br.advfn.com/p.php?pid=charts](http://br.advfn.com/p.php?pid=charts)
Use some code to chart like GOOG
6. The applet works for about 5 seconds and firefox crash with this log:
```

Unexpected Signal : 11 occurred at PC=0x2B827778ADAA
Function=(null)+0x7778ADAA
Library=/usr/lib/j2se/1.4/jre/lib/amd64/server/libjvm.so

NOTE: We are unable to locate the function name symbol for the error
      just occurred. Please refer to release documentation for possible
      reason and solutions.


Current Java thread:
        at sun.plugin.navig.motif.AThread.handleRequest(Native Method)
        at sun.plugin.navig.motif.AThread.JNIHandleLoop(AThread.java:35)
        at sun.plugin.navig.motif.AThread.run(AThread.java:27)

Dynamic libraries:
40000000-40003000 r-xp 00000000 08:08 3140445                            /usr/lib/j2se/1.4/jre/bin/java_vm
40102000-40103000 rwxp 00002000 08:08 3140445                            /usr/lib/j2se/1.4/jre/bin/java_vm
40103000-4018f000 rwxp 40103000 00:00 0                                  [heap]
2aaaaaaac000-2aaaaaaeb000 r-xp 00000000 08:08 3074411                    /usr/lib/locale/pt_BR.utf8/LC_CTYPE
2aaaaaaeb000-2aaaaaaf2000 r-xs 00000000 08:08 3646738                    /usr/lib/gconv/gconv-modules.cache
2aaaaaaf2000-2aaaaabf2000 rwxp 2aaaaaaf2000 00:00 0 
2aaaaabf2000-2aaaaac00000 r-xs 00000000 08:08 3140862                    /usr/lib/j2se/1.4/jre/lib/ext/ldapsec.jar
2aaaaac00000-2aaaaac03000 r-xs 00000000 08:08 3140860                    /usr/lib/j2se/1.4/jre/lib/ext/dnsns.jar
2aaaaac03000-2aaaaac1f000 r-xs 00000000 08:08 3140861                    /usr/lib/j2se/1.4/jre/lib/ext/sunjce_provider.jar
2aaaaac1f000-2aaaaacdb000 r-xs 00000000 08:08 3140863                    /usr/lib/j2se/1.4/jre/lib/ext/localedata.jar
2aaaaacdb000-2aaaaadbe000 r-xp 00000000 08:08 3140893                    /usr/lib/j2se/1.4/jre/lib/amd64/libawt.so
2aaaaadbe000-2aaaaaebf000 ---p 000e3000 08:08 3140893                    /usr/lib/j2se/1.4/jre/lib/amd64/libawt.so
2aaaaaebf000-2aaaaaee0000 rwxp 000e4000 08:08 3140893                    /usr/lib/j2se/1.4/jre/lib/amd64/libawt.so
2aaaaaee0000-2aaaaaf05000 rwxp 2aaaaaee0000 00:00 0 
2aaaaaf05000-2aaaaaf5d000 r-xp 00000000 08:08 3140880                    /usr/lib/j2se/1.4/jre/lib/amd64/libmlib_image.so
2aaaaaf5d000-2aaaab05d000 ---p 00058000 08:08 3140880                    /usr/lib/j2se/1.4/jre/lib/amd64/libmlib_image.so
2aaaab05d000-2aaaab060000 rwxp 00058000 08:08 3140880                    /usr/lib/j2se/1.4/jre/lib/amd64/libmlib_image.so
2aaaab060000-2aaaab2a5000 r-xp 00000000 08:08 3140864                    /usr/lib/j2se/1.4/jre/lib/amd64/libXm.so.3
2aaaab2a5000-2aaaab3a4000 ---p 00245000 08:08 3140864                    /usr/lib/j2se/1.4/jre/lib/amd64/libXm.so.3
2aaaab3a4000-2aaaab40e000 rwxp 00244000 08:08 3140864                    /usr/lib/j2se/1.4/jre/lib/amd64/libXm.so.3
2aaaab40e000-2aaaab40f000 rwxp 2aaaab40e000 00:00 0 
2aaaab423000-2aaaab42b000 r-xp 00000000 08:08 3025333                    /usr/lib/libXp.so.6.2.0
2aaaab42b000-2aaaab62b000 ---p 00008000 08:08 3025333                    /usr/lib/libXp.so.6.2.0
2aaaab62b000-2aaaab62c000 rwxp 00008000 08:08 3025333                    /usr/lib/libXp.so.6.2.0
2aaaab62c000-2aaaab689000 r-xp 00000000 08:08 3025334                    /usr/lib/libXt.so.6.0.0
2aaaab689000-2aaaab889000 ---p 0005d000 08:08 3025334                    /usr/lib/libXt.so.6.0.0
2aaaab889000-2aaaab88f000 rwxp 0005d000 08:08 3025334                    /usr/lib/libXt.so.6.0.0
2aaaab88f000-2aaaab890000 rwxp 2aaaab88f000 00:00 0 
2aaaab890000-2aaaab898000 r-xp 00000000 08:08 3026423                    /usr/lib/libSM.so.6.0.0
2aaaab898000-2aaaaba97000 ---p 00008000 08:08 3026423                    /usr/lib/libSM.so.6.0.0
2aaaaba97000-2aaaaba98000 rwxp 00007000 08:08 3026423                    /usr/lib/libSM.so.6.0.0
2aaaaba98000-2aaaabaaf000 r-xp 00000000 08:08 3025295                    /usr/lib/libICE.so.6.3.0
2aaaabaaf000-2aaaabcaf000 ---p 00017000 08:08 3025295                    /usr/lib/libICE.so.6.3.0
2aaaabcaf000-2aaaabcb0000 rwxp 00017000 08:08 3025295                    /usr/lib/libICE.so.6.3.0
2aaaabcb0000-2aaaabcb4000 rwxp 2aaaabcb0000 00:00 0 
2aaaabcb4000-2aaaabcc5000 r-xp 00000000 08:08 3026458                    /usr/lib/libXext.so.6.4.0
2aaaabcc5000-2aaaabec4000 ---p 00011000 08:08 3026458                    /usr/lib/libXext.so.6.4.0
2aaaabec4000-2aaaabec5000 rwxp 00010000 08:08 3026458                    /usr/lib/libXext.so.6.4.0
2aaaabec5000-2aaaabeca000 r-xp 00000000 08:08 3025330                    /usr/lib/libXtst.so.6.1.0
2aaaabeca000-2aaaac0ca000 ---p 00005000 08:08 3025330                    /usr/lib/libXtst.so.6.1.0
2aaaac0ca000-2aaaac0cb000 rwxp 00005000 08:08 3025330                    /usr/lib/libXtst.so.6.1.0
2aaaac0cb000-2aaaac1d5000 r-xp 00000000 08:08 3026421                    /usr/lib/libX11.so.6.2.0
2aaaac1d5000-2aaaac3d5000 ---p 0010a000 08:08 3026421                    /usr/lib/libX11.so.6.2.0
2aaaac3d5000-2aaaac3dc000 rwxp 0010a000 08:08 3026421                    /usr/lib/libX11.so.6.2.0
2aaaac3dc000-2aaaac3de000 r-xp 00000000 08:08 3025882                    /usr/lib/libXau.so.6.0.0
2aaaac3de000-2aaaac5dd000 ---p 00002000 08:08 3025882                    /usr/lib/libXau.so.6.0.0
2aaaac5dd000-2aaaac5de000 rwxp 00001000 08:08 3025882                    /usr/lib/libXau.so.6.0.0
2aaaac5de000-2aaaac5e3000 r-xp 00000000 08:08 3026415                    /usr/lib/libXdmcp.so.6.0.0
2aaaac5e3000-2aaaac7e2000 ---p 00005000 08:08 3026415                    /usr/lib/libXdmcp.so.6.0.0
2aaaac7e2000-2aaaac7e3000 rwxp 00004000 08:08 3026415                    /usr/lib/libXdmcp.so.6.0.0
2aaaac7e3000-2aaaac7f4000 r-xp 00000000 08:08 3140892                    /usr/lib/j2se/1.4/jre/lib/amd64/libjavaplugin_jni.so
2aaaac7f4000-2aaaac8f3000 ---p 00011000 08:08 3140892                    /usr/lib/j2se/1.4/jre/lib/amd64/libjavaplugin_jni.so
2aaaac8f3000-2aaaac8f6000 rwxp 00010000 08:08 3140892                    /usr/lib/j2se/1.4/jre/lib/amd64/libjavaplugin_jni.so
2aaaac8f6000-2aaaac91e000 rwxp 2aaaac8f6000 00:00 0 
2aaaac91e000-2aaaac9bb000 r-xp 00000000 08:08 3140874                    /usr/lib/j2se/1.4/jre/lib/amd64/libfontmanager.so
2aaaac9bb000-2aaaacaba000 ---p 0009d000 08:08 3140874                    /usr/lib/j2se/1.4/jre/lib/amd64/libfontmanager.so
2aaaacaba000-2aaaacad9000 rwxp 0009c000 08:08 3140874                    /usr/lib/j2se/1.4/jre/lib/amd64/libfontmanager.so
2aaaacad9000-2aaaacaea000 rwxp 2aaaacad9000 00:00 0 
2aaaacb1b000-2aaaacd1b000 rwxp 2aaaacb1b000 00:00 0 
2aaaacd2f000-2aaaacd39000 r-xp 00000000 08:08 3026497                    /usr/lib/libXcursor.so.1.0.2
2aaaacd39000-2aaaacf38000 ---p 0000a000 08:08 3026497                    /usr/lib/libXcursor.so.1.0.2
2aaaacf38000-2aaaacf39000 rwxp 00009000 08:08 3026497                    /usr/lib/libXcursor.so.1.0.2
2aaaacf39000-2aaaacf42000 r-xp 00000000 08:08 3058460                    /usr/lib/libXrender.so.1.3.0
2aaaacf42000-2aaaad141000 ---p 00009000 08:08 3058460                    /usr/lib/libXrender.so.1.3.0
2aaaad141000-2aaaad142000 rwxp 00008000 08:08 3058460                    /usr/lib/libXrender.so.1.3.0
2aaaad142000-2aaaad147000 r-xp 00000000 08:08 3026454                    /usr/lib/libXfixes.so.3.1.0
2aaaad147000-2aaaad346000 ---p 00005000 08:08 3026454                    /usr/lib/libXfixes.so.3.1.0
2aaaad346000-2aaaad347000 rwxp 00004000 08:08 3026454                    /usr/lib/libXfixes.so.3.1.0
2aaaad3ec000-2aaaad4ec000 rwxp 2aaaad3ec000 00:00 0 
2aaaad4ec000-2aaaad4f3000 r-xs 00000000 08:07 473833                     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2aaaad4f3000-2aaaad4f8000 r-xs 00000000 08:07 473798                     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2aaaad4f8000-2aaaad4fe000 r-xs 00000000 08:07 473837                     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86-64.cache-2
2aaaad4fe000-2aaaad509000 r-xs 00000000 08:07 473835                     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86-64.cache-2
2aaaad509000-2aaaad50a000 r-xs 00000000 08:07 473838                     /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86-64.cache-2
2aaaad50a000-2aaaad512000 r-xs 00000000 08:07 473805                     /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86-64.cache-2
2aaaad512000-2aaaad519000 r-xs 00000000 08:07 473839                     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86-64.cache-2
2aaaad519000-2aaaad51b000 r-xs 00000000 08:07 472500                     /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86-64.cache-2
2aaaad51b000-2aaaad51c000 r-xs 00000000 08:07 472526                     /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86-64.cache-2
2aaaad51c000-2aaaad51d000 r-xs 00000000 08:07 473807                     /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86-64.cache-2
2aaaad51d000-2aaaad521000 r-xs 00000000 08:07 472499                     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86-64.cache-2
2aaaad521000-2aaaad524000 r-xs 00000000 08:07 472529                     /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86-64.cache-2
2aaaad524000-2aaaad52a000 r-xs 00000000 08:07 473802                     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86-64.cache-2
2aaaad52a000-2aaaad531000 r-xs 00000000 08:07 472530                     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86-64.cache-2
2aaaad531000-2aaaad532000 r-xs 00000000 08:07 472531                     /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86-64.cache-2
2aaaad532000-2aaaad535000 r-xs 00000000 08:07 473800                     /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86-64.cache-2
2aaaad535000-2aaaad536000 r-xs 00000000 08:07 472438                     /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86-64.cache-2
2aaaad536000-2aaaad539000 r-xs 00000000 08:07 472504                     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86-64.cache-2
2aaaad539000-2aaaad544000 r-xs 00000000 08:07 473794                     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86-64.cache-2
2aaaad544000-2aaaad548000 r-xs 00000000 08:07 473806                     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86-64.cache-2
2aaaad548000-2aaaad54b000 r-xs 00000000 08:07 473796                     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86-64.cache-2
2aaaad54b000-2aaaad54c000 r-xs 00000000 08:07 473808                     /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86-64.cache-2
2aaaad54c000-2aaaad54d000 r-xs 00000000 08:07 473809                     /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86-64.cache-2
2aaaad54d000-2aaaad54e000 r-xs 00000000 08:07 473811                     /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86-64.cache-2
2aaaad54e000-2aaaad54f000 r-xs 00000000 08:07 473799                     /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86-64.cache-2
2aaaad54f000-2aaaad559000 r-xs 00000000 08:07 473836                     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86-64.cache-2
2aaaad559000-2aaaad55e000 r-xs 00000000 08:07 472727                     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
2aaaad55e000-2aaaad562000 r-xs 00000000 08:07 473793                     /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86-64.cache-2
2aaaad562000-2aaaad569000 r-xs 00000000 08:07 472571                     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
2aaaad569000-2aaaad56c000 r-xs 00000000 08:07 472563                     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
2aaaad56c000-2aaaad58b000 r-xs 00000000 08:07 472502                     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86-64.cache-2
2aaaad58b000-2aaaad58c000 r-xs 00000000 08:07 472501                     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
2aaaad58c000-2aaaad594000 r-xs 00000000 08:07 473810                     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
2aaaad594000-2aaaad59f000 r-xs 00000000 08:07 473812                     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
2aaaad59f000-2aaaad5a1000 r-xs 00000000 08:07 473813                     /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86-64.cache-2
2aaaad5a1000-2aaaad5a4000 r-xs 00000000 08:07 473814                     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
2aaaad5a4000-2aaaad5ac000 r-xs 00000000 08:07 473815                     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
2aaaad5ac000-2aaaad5af000 r-xs 00000000 08:07 473816                     /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86-64.cache-2
2aaaad5af000-2aaaad5b1000 r-xs 00000000 08:07 473817                     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86-64.cache-2
2aaaad5b1000-2aaaad5b3000 r-xs 00000000 08:07 473818                     /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86-64.cache-2
2aaaad5b3000-2aaaad5b7000 r-xs 00000000 08:07 473819                     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
2aaaad5b7000-2aaaad5b9000 r-xs 00000000 08:07 473820                     /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86-64.cache-2
2aaaad5b9000-2aaaad5ba000 r-xs 00000000 08:07 473821                     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
2aaaad5ba000-2aaaad5bb000 r-xs 00000000 08:07 473822                     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86-64.cache-2
2aaaad5bb000-2aaaad5c0000 r-xs 00000000 08:07 473823                     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86-64.cache-2
2aaaad5c0000-2aaaad5c1000 r-xs 00000000 08:07 473824                     /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86-64.cache-2
2aaaad5c1000-2aaaad5c2000 r-xs 00000000 08:07 473825                     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86-64.cache-2
2aaaad5c2000-2aaaad5c5000 r-xs 00000000 08:07 473826                     /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86-64.cache-2
2aaaad5c5000-2aaaad5c6000 r-xs 00000000 08:07 473827                     /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86-64.cache-2
2aaaad5c6000-2aaaad5c9000 r-xs 00000000 08:07 473828                     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86-64.cache-2
2aaaad5c9000-2aaaad5d1000 r-xs 00000000 08:07 473830                     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
2aaaad5d1000-2aaaad8d1000 rwxp 2aaaad5d1000 00:00 0 
2aaaad8d1000-2aaaad8df000 r-xp 00000000 08:08 3140865                    /usr/lib/j2se/1.4/jre/lib/amd64/libnet.so
2aaaad8df000-2aaaad9de000 ---p 0000e000 08:08 3140865                    /usr/lib/j2se/1.4/jre/lib/amd64/libnet.so
2aaaad9de000-2aaaad9e1000 rwxp 0000d000 08:08 3140865                    /usr/lib/j2se/1.4/jre/lib/amd64/libnet.so
2aaaad9e2000-2aaaad9fb000 r-xp 00000000 08:08 3140887                    /usr/lib/j2se/1.4/jre/lib/amd64/libdcpr.so
2aaaad9fb000-2aaaadafa000 ---p 00019000 08:08 3140887                    /usr/lib/j2se/1.4/jre/lib/amd64/libdcpr.so
2aaaadafa000-2aaaadb11000 rwxp 00018000 08:08 3140887                    /usr/lib/j2se/1.4/jre/lib/amd64/libdcpr.so
2aaaadb25000-2aaaadb27000 r-xp 00000000 08:05 127663                     /lib/libnss_mdns4_minimal.so.2
2aaaadb27000-2aaaadd26000 ---p 00002000 08:05 127663                     /lib/libnss_mdns4_minimal.so.2
2aaaadd26000-2aaaadd27000 rwxp 00001000 08:05 127663                     /lib/libnss_mdns4_minimal.so.2
2aaaadd27000-2aaaadd2b000 r-xp 00000000 08:05 127812                     /lib/libnss_dns-2.6.1.so
2aaaadd2b000-2aaaadf2b000 ---p 00004000 08:05 127812                     /lib/libnss_dns-2.6.1.so
2aaaadf2b000-2aaaadf2d000 rwxp 00004000 08:05 127812                     /lib/libnss_dns-2.6.1.so
2aaaadf2d000-2aaaadf3f000 r-xp 00000000 08:05 127819                     /lib/libresolv-2.6.1.so
2aaaadf3f000-2aaaae13e000 ---p 00012000 08:05 127819                     /lib/libresolv-2.6.1.so
2aaaae13e000-2aaaae140000 rwxp 00011000 08:05 127819                     /lib/libresolv-2.6.1.so
2aaaae140000-2aaaaea71000 rwxp 2aaaae140000 00:00 0 
2aaaaea71000-2aaaaea77000 r-xs 00000000 08:06 16                         /tmp/jar_cache11871.tmp (deleted)
2aaaaea77000-2aaaaea78000 rwxp 2aaaaea77000 00:00 0 
2aaab0000000-2aaab0b9a000 rwxp 2aaab0000000 00:00 0 
2aaab0b9a000-2aaab4000000 ---p 2aaab0b9a000 00:00 0 
2b8276ac0000-2b8276add000 r-xp 00000000 08:05 127492                     /lib/ld-2.6.1.so
2b8276add000-2b8276ae0000 rwxp 2b8276add000 00:00 0 
2b8276cdc000-2b8276cde000 rwxp 0001c000 08:05 127492                     /lib/ld-2.6.1.so
2b8276cde000-2b8276cf4000 r-xp 00000000 08:05 127818                     /lib/libpthread-2.6.1.so
2b8276cf4000-2b8276ef3000 ---p 00016000 08:05 127818                     /lib/libpthread-2.6.1.so
2b8276ef3000-2b8276ef5000 rwxp 00015000 08:05 127818                     /lib/libpthread-2.6.1.so
2b8276ef5000-2b8276ef9000 rwxp 2b8276ef5000 00:00 0 
2b8276ef9000-2b8276efb000 r-xp 00000000 08:05 127807                     /lib/libdl-2.6.1.so
2b8276efb000-2b82770fb000 ---p 00002000 08:05 127807                     /lib/libdl-2.6.1.so
2b82770fb000-2b82770fd000 rwxp 00002000 08:05 127807                     /lib/libdl-2.6.1.so
2b82770fd000-2b827724f000 r-xp 00000000 08:05 127804                     /lib/libc-2.6.1.so
2b827724f000-2b827744e000 ---p 00152000 08:05 127804                     /lib/libc-2.6.1.so
2b827744e000-2b8277451000 r-xp 00151000 08:05 127804                     /lib/libc-2.6.1.so
2b8277451000-2b8277453000 rwxp 00154000 08:05 127804                     /lib/libc-2.6.1.so
2b8277453000-2b827745a000 rwxp 2b8277453000 00:00 0 
2b827745a000-2b8277999000 r-xp 00000000 08:08 3189009                    /usr/lib/j2se/1.4/jre/lib/amd64/server/libjvm.so
2b8277999000-2b8277a9a000 ---p 0053f000 08:08 3189009                    /usr/lib/j2se/1.4/jre/lib/amd64/server/libjvm.so
2b8277a9a000-2b8277bc6000 rwxp 00540000 08:08 3189009                    /usr/lib/j2se/1.4/jre/lib/amd64/server/libjvm.so
2b8277bc6000-2b8277bf8000 rwxp 2b8277bc6000 00:00 0 
2b8277c0c000-2b8277c22000 r-xp 00000000 08:05 127810                     /lib/libnsl-2.6.1.so
2b8277c22000-2b8277e21000 ---p 00016000 08:05 127810                     /lib/libnsl-2.6.1.so
2b8277e21000-2b8277e23000 rwxp 00015000 08:05 127810                     /lib/libnsl-2.6.1.so
2b8277e23000-2b8277e25000 rwxp 2b8277e23000 00:00 0 
2b8277e25000-2b8277ea5000 r-xp 00000000 08:05 127808                     /lib/libm-2.6.1.so
2b8277ea5000-2b82780a4000 ---p 00080000 08:05 127808                     /lib/libm-2.6.1.so
2b82780a4000-2b82780a6000 rwxp 0007f000 08:05 127808                     /lib/libm-2.6.1.so
2b82780a6000-2b82780ae000 r-xp 00000000 08:08 3140877                    /usr/lib/j2se/1.4/jre/lib/amd64/native_threads/libhpi.so
2b82780ae000-2b82781ae000 ---p 00008000 08:08 3140877                    /usr/lib/j2se/1.4/jre/lib/amd64/native_threads/libhpi.so
2b82781ae000-2b82781b0000 rwxp 00008000 08:08 3140877                    /usr/lib/j2se/1.4/jre/lib/amd64/native_threads/libhpi.so
2b82781b0000-2b82781b1000 rwxp 2b82781b0000 00:00 0 
2b82781b1000-2b82781b5000 rwxs 00000000 08:06 45988                      /tmp/hsperfdata_fred/7461
2b82781c5000-2b82781cd000 r-xp 00000000 08:05 127811                     /lib/libnss_compat-2.6.1.so
2b82781cd000-2b82783cc000 ---p 00008000 08:05 127811                     /lib/libnss_compat-2.6.1.so
2b82783cc000-2b82783ce000 rwxp 00007000 08:05 127811                     /lib/libnss_compat-2.6.1.so
2b82783ce000-2b82783d8000 r-xp 00000000 08:05 127815                     /lib/libnss_nis-2.6.1.so
2b82783d8000-2b82785d7000 ---p 0000a000 08:05 127815                     /lib/libnss_nis-2.6.1.so
2b82785d7000-2b82785d9000 rwxp 00009000 08:05 127815                     /lib/libnss_nis-2.6.1.so
2b82785d9000-2b82785e3000 r-xp 00000000 08:05 127813                     /lib/libnss_files-2.6.1.so
2b82785e3000-2b82787e2000 ---p 0000a000 08:05 127813                     /lib/libnss_files-2.6.1.so
2b82787e2000-2b82787e4000 rwxp 00009000 08:05 127813                     /lib/libnss_files-2.6.1.so
2b82787e4000-2b82787f6000 r-xp 00000000 08:08 3140869                    /usr/lib/j2se/1.4/jre/lib/amd64/libverify.so
2b82787f6000-2b82788f5000 ---p 00012000 08:08 3140869                    /usr/lib/j2se/1.4/jre/lib/amd64/libverify.so
2b82788f5000-2b82788f8000 rwxp 00011000 08:08 3140869                    /usr/lib/j2se/1.4/jre/lib/amd64/libverify.so
2b82788f8000-2b8278918000 r-xp 00000000 08:08 3140882                    /usr/lib/j2se/1.4/jre/lib/amd64/libjava.so
2b8278918000-2b8278a18000 ---p 00020000 08:08 3140882                    /usr/lib/j2se/1.4/jre/lib/amd64/libjava.so
2b8278a18000-2b8278a1d000 rwxp 00020000 08:08 3140882                    /usr/lib/j2se/1.4/jre/lib/amd64/libjava.so
2b8278a1d000-2b8278a2e000 r-xp 00000000 08:08 3140876                    /usr/lib/j2se/1.4/jre/lib/amd64/libzip.so
2b8278a2e000-2b8278b2d000 ---p 00011000 08:08 3140876                    /usr/lib/j2se/1.4/jre/lib/amd64/libzip.so
2b8278b2d000-2b8278b31000 rwxp 00010000 08:08 3140876                    /usr/lib/j2se/1.4/jre/lib/amd64/libzip.so
2b8278b31000-2b827a4dd000 r-xs 00000000 08:08 3140902                    /usr/lib/j2se/1.4/jre/lib/rt.jar
2b827a4dd000-2b827a527000 rwxp 2b827a4dd000 00:00 0 
2b827a527000-2b827a53d000 r-xs 00000000 08:08 3140898                    /usr/lib/j2se/1.4/jre/lib/sunrsasign.jar
2b827a53d000-2b827a61a000 r-xs 00000000 08:08 3140895                    /usr/lib/j2se/1.4/jre/lib/jsse.jar
2b827a61a000-2b827a62b000 r-xs 00000000 08:08 3140900                    /usr/lib/j2se/1.4/jre/lib/jce.jar
2b827a62b000-2b827abcb000 r-xs 00000000 08:08 3140896                    /usr/lib/j2se/1.4/jre/lib/charsets.jar
2b827abcb000-2b827adad000 r-xs 00000000 08:08 3140897                    /usr/lib/j2se/1.4/jre/lib/plugin.jar
2b827adad000-2b827aead000 rwxp 2b827adad000 00:00 0 
2b827aead000-2b82badad000 rwxp 2b827aead000 00:00 0 
2b82badad000-2b82badb1000 rwxp 2b82badad000 00:00 0 
2b82badb1000-2b82bbdad000 rwxp 2b82badb1000 00:00 0 
2b82bbdad000-2b82bbdfc000 rwxp 2b82bbdad000 00:00 0 
2b82bbe00000-2b82bc360000 rwxp 2b82bbe00000 00:00 0 
2b82bc360000-2b82bd350000 rwxp 2b82bc360000 00:00 0 
2b82bd350000-2b82bddea000 rwxp 2b82bd350000 00:00 0 
2b82bddea000-2b82bfe00000 rwxp 2b82bddea000 00:00 0 
2b82bfe00000-2b82c0e00000 rwxp 2b82bfe00000 00:00 0 
2b82c0e00000-2b82c3e00000 rwxp 2b82c0e00000 00:00 0 
2b82c3e00000-2b82c3e03000 rwxp 2b82c3e00000 00:00 0 
2b82c3e03000-2b82c3e0a000 rwxp 2b82c3e03000 00:00 0 
2b82c3e0a000-2b82c3e10000 rwxp 2b82c3e0a000 00:00 0 
2b82c3e10000-2b82c3e20000 rwxp 2b82c3e10000 00:00 0 
2b82c3e20000-2b82c3e28000 rwxp 2b82c3e20000 00:00 0 
2b82c3e28000-2b82c3e40000 rwxp 2b82c3e28000 00:00 0 
2b82c3e40000-2b82c3e47000 rwxp 2b82c3e40000 00:00 0 
2b82c3e47000-2b82c3e57000 rwxp 2b82c3e47000 00:00 0 
2b82c3e57000-2b82c3e60000 rwxp 2b82c3e57000 00:00 0 
2b82c3e60000-2b82c3e78000 rwxp 2b82c3e60000 00:00 0 
7fff33dea000-7fff33dec000 rwxp 7fff33dea000 00:00 0 
7fff33dec000-7fff33def000 ---p 7fff33dec000 00:00 0 
7fff33fc5000-7fff33fea000 rwxp 7fff33fc5000 00:00 0                      [stack]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]

Heap at VM Abort:
Heap
 def new generation   total 4992K, used 16K [0x00002b82bbe00000, 0x00002b82bc360000, 0x00002b82bd350000)
  eden space 4480K,   0% used [0x00002b82bbe00000, 0x00002b82bbe042a8, 0x00002b82bc260000)
  from space 512K,   0% used [0x00002b82bc260000, 0x00002b82bc260000, 0x00002b82bc2e0000)
  to   space 512K,   0% used [0x00002b82bc2e0000, 0x00002b82bc2e0000, 0x00002b82bc360000)
 tenured generation   total 10856K, used 4211K [0x00002b82bd350000, 0x00002b82bddea000, 0x00002b82bfe00000)
   the space 10856K,  38% used [0x00002b82bd350000, 0x00002b82bd76cc38, 0x00002b82bd76ce00, 0x00002b82bddea000)
 compacting perm gen  total 16384K, used 11427K [0x00002b82bfe00000, 0x00002b82c0e00000, 0x00002b82c3e00000)
   the space 16384K,  69% used [0x00002b82bfe00000, 0x00002b82c0928c38, 0x00002b82c0928e00, 0x00002b82c0e00000)

Local Time = Sun Oct 28 09:08:08 2007
Elapsed Time = 110
#
# HotSpot Virtual Machine Error : 11
# Error ID : 4F530E43505002EF
# Please report this error at
# http://www.blackdown.org/cgi-bin/jdk
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (Blackdown-1.4.2-02 mixed mode)
#
# An error report file has been saved as hs_err_pid7461.log.
# Please refer to the file for further information.
#
Plugin: unexpected work request from child
INTERNAL ERROR on Browser End: Code = aa2a0000
System error?:: Sucesso
```

Now I will try these steps with IcedTea.

Hey man, I think it is COOL to crash a browser.
Could you go to some more simple site to test your Java JVM. If it passed, that means you're OK. I do try your all very special link, it ate my CPU resource very hard.
I think it might be a) the firefox fault or b) the designer of the site
Give more try and test, and show your result.

Oh, by the way, after I took a look at the error code, I think your memory to and from CPU might not stable.
You might have hardware problem.

---

### Post by fredbeltrao on 2007-10-28
> **jenhsun said:**
> Hey man, I think it is COOL to crash a browser.
Could you go to some more simple site to test your Java JVM. If it passed, that means you're OK. I do try your all very special link, it ate my CPU resource very hard.
I think it might be a) the firefox fault or b) the designer of the site
Give more try and test, and show your result.

Oh, by the way, after I took a look at the error code, I think your memory to and from CPU might not stable.
You might have hardware problem.

Hi jenhsun,

I really appreciate your help on this thread. But I must tell you that I access this applet []http://br.advfn.com/p.php?pid=charts]("http://br.advfn.com/p.php?pid=charts") not just for dumb test... I need to access this especific applet because I need to monitor the stock market... If I cannot access this applet, it's better for me to turn back to Ubuntu 7.04 or pehaps to go back to Windows XP. This applet works on my box before I update to 7.10. When I was on 7.04 and firefox32 it works perfect when I use [this amazing post]("http://ubuntuforums.org/showthread.php?t=202537") to solve my problem. I will use that post again, since the guy has updated the script to work on gutsy.

Thanks for your help.

---

### Post by jenhsun on 2007-10-28
> **fredbeltrao said:**
> Hi jenhsun,

I really appreciate your help on this thread. But I must tell you that I access this applet []http://br.advfn.com/p.php?pid=charts]("http://br.advfn.com/p.php?pid=charts") not just for dumb test... I need to access this especific applet because I need to monitor the stock market... If I cannot access this applet, it's better for me to turn back to Ubuntu 7.04 or pehaps to go back to Windows XP. This applet works on my box before I update to 7.10. When I was on 7.04 and firefox32 it works perfect when I use [this amazing post]("http://ubuntuforums.org/showthread.php?t=202537") to solve my problem. I will use that post again, since the guy has updated the script to work on gutsy.

Thanks for your help.

No problem at all, this is the sharing community.
I took a look at that thread before, however, I just need to solve and truely understand the problem is. 
By the way, downgrade your system is a good decision. We currently have so many performance issue in Gutsy, not to mention 32 or 64 bits.
Good Luck.

---

### Post by fredbeltrao on 2007-10-28
Problem solved with [this thread]("http://ubuntuforums.org/showthread.php?t=202537").

Just download the script, unzip, double click and fallow de instructions...

Result:
Firefox32 and jvm 1.6 (also 32) installed and working.

Thank you all and jenhsun for help,

Fred

---

### Post by jenhsun on 2007-10-28
> **fredbeltrao said:**
> Problem solved with [this thread]("http://ubuntuforums.org/showthread.php?t=202537").

Just download the script, unzip, double click and fallow de instructions...

Result:
Firefox32 and jvm 1.6 (also 32) installed and working.

Thank you all and jenhsun for help,

Fred

No problem, Fred.
Good to see your firefox works.
For people who don't want to stay on firefox64 in 64 bits OS, change to firefox32 is a solution for most of the plugin.

---

### Post by snkmad on 2007-10-30
> **skylark said:**
> I had the same problem. I fixed it by adding the unofficial iced-tea gutsy repository to my apt sources. I did this by appending the following lines to /etc/apt/sources.list (and then doing the usual update and upgrade):

```
# iced-tea updates
deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
```

I have noticed it can a while for some plugins to start though (up to 10 seconds with my setup) but at least they seem to work.

Im trying this now, gonna reply if everything works in a few...
Yeah its working!
Tried the [www.java.com](www.java.com) site, it said java 1.7.0 sucessfully instaled, and also tried Runescape.
Indeed it took sometime to load, and also it said it couldnt make a cache of the game, i had to use the unsignet java option. And ingame i could only hear music, but no char sounds...

---

### Post by wwright on 2007-11-02
ok I followed this post to the best of my abilities and I am still having no luck. Trying to Test JAVA is doing nothing. Still telling me to install the plugin. When I click it gives me the error saying the plugin is already isntalled. I added the other repository updated installed. I´ve tried making sure no other versions were installed and to my knowledge I have removed everything else. 

SOMEONE HELP

---

### Post by American_Outcast on 2007-11-02
> **wwright said:**
> ok I followed this post to the best of my abilities and I am still having no luck. Trying to Test JAVA is doing nothing. Still telling me to install the plugin. When I click it gives me the error saying the plugin is already isntalled. I added the other repository updated installed. I´ve tried making sure no other versions were installed and to my knowledge I have removed everything else. 

SOMEONE HELP


Your not alone with this. No matter what I do Java just doesn't want to work for me. But in Sabayon 64bit it works great, LiveDVD or installed system.

---

### Post by dcstar on 2007-11-02
> **wwright said:**
> ok I followed this post to the best of my abilities and I am still having no luck. Trying to Test JAVA is doing nothing. Still telling me to install the plugin. When I click it gives me the error saying the plugin is already isntalled. I added the other repository updated installed. I´ve tried making sure no other versions were installed and to my knowledge I have removed everything else. 

SOMEONE HELP

In Firefox, enter **about: plugins** (get rid of the space) to see what it thinks it has available.

You may see more than one plugin to handle Java, if so then post the relevant info here so we can have a look at it.

---

### Post by wwright on 2007-11-02
I already did the about: plugins thing and there are no java plugins installed. It stays that way no matter what version I´m trying to install....

I seem to think I´m following all the steps properly, although I am still rather new to linux/ubuntu

---

### Post by ruru on 2007-11-03
I just tried adding the unofficial iced-tea repository, uninstalled and then reinstalled all the icedtea packages - and now it works fine. Just adding the new repository and updating didn't seem to do it for me...
p.s. this is in firefox 2.0.0.8 on xubuntu 7.10 AMD64.

---

### Post by wwright on 2007-11-03
Java seems to be working fine now. I went through and did a few more tweaks and something along the line seemed to have worked out for me. 

Now the main reason I was trying to get the java working is so my girlfriend can play the games at [www.pogo.com](www.pogo.com) 

So every java tester on the web seems to be working flawlessly, yet pogo.com games still fail to load. ANY ideas?

---

### Post by American_Outcast on 2007-11-03
> **wwright said:**
> Java seems to be working fine now. I went through and did a few more tweaks and something along the line seemed to have worked out for me. 

Now the main reason I was trying to get the java working is so my girlfriend can play the games at [www.pogo.com]("http://www.pogo.com") 

So every java tester on the web seems to be working flawlessly, yet pogo.com games still fail to load. ANY ideas?


Are you sure Java is the problem? If you are blocking pop ups Pogo won't work at all.

---

### Post by wwright on 2007-11-04
no the pop up window opens just fine says loading, It never loads and then tells me java is not detected or configured properly. Yet everything else java I´ve had no problems with

---

### Post by Soarer on 2007-11-05
It doesn't help you I know, but the games popups load for me. I am not a registered user though, so I haven't actually played any, just seen the demos.

FYI I am using Iced Tea Java & non-free flash on 64 bit FF on Gutsy.

---

### Post by jw5801 on 2007-11-14
> **wwright said:**
> Java seems to be working fine now. I went through and did a few more tweaks and something along the line seemed to have worked out for me.

...

What did you do to get firefox to recognise the java plugin? I can't for the life of me get it to even appear in about: plugins at all, there's no mention of java on the page anywhere. icedtea-java7-plugin (and it's dependencies) is the only java package I have installed. The others (gcj and sun-java6) have been removed and purged.

---

### Post by d1ss0nant on 2007-11-14
I have also been driven CRAZY by not being able to get Java to work in firefox!  I have tried the regular java plugin, icedtea, and another that i found in synaptic.  I am so frustrated.  I wish someone could find a solution :(

---

### Post by treacle boy on 2007-11-16
Hello folks,

I too am running a 64bit version of Gutsy on my box which uses a AMD Athlon 64 3000+ processor. I would dearly like to run Azureus as I have found bit torrent stops without explanation during large (GB+) downloads. After initially installing Azureus I found that it had issues with my java software, following this thread I have suceeded in installing Iced Tea via synaptic:

```
treacle@ubuntu:~$ java -version
java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b22)
IcedTea 64-Bit Server VM (build 1.7.0-b22, mixed mode)

```

I then updated the repositories list to include the ice-tea updates (see previous post) and ran an update (sudo apt-get update). 

I upgraded the ice-tea installation using synaptic. This is what I got when I tried to run Azureus
:
```

treacle@ubuntu:~$ azureus
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b728fc730ff, pid=6904, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b22 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x33b0ff]
#
# An error report file with more information is saved as:
# /home/treacle/.azureus/hs_err_pid6904.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
Aborted (core dumped)
```

I tried uninstalling and reinstalling Iced-tea (icedtea-java7-bin, icedtea-java7-doc, icedtea-java7-jdk, icedtea-java7-jre, icedtea-java7-plugin and icedtea-java7-source) through synaptic but I still hit the same brick wall when trying to run Azureus.

Does anyone have any ideas?

cheers,

Treacle Boy :confused:

---

### Post by angryfirelord on 2007-11-16
Uninstall the icedtea packages and install the sun-java6 packages. If it works, then there's still some issues with icedtea that have to be resolved. I've noticed that there are issues with icedtea still popping up in the fedora forums as well. 

Please also note that if you do revert back to sun-java6, you'll lose the firefox plugin.

---

### Post by imlepid on 2007-11-16
Hey folks.  I am having a little trouble getting Java applets fully working.  I have installed the icedtea-java7 plusins and have some sites working (for example [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) ) while on other sites the applet starts to load but stops with the error "Start: applet not initialized."  (e.g. this site [http://www.dailyfx.com/charts/Chart.html?symbol=EUR/USD](http://www.dailyfx.com/charts/Chart.html?symbol=EUR/USD) )

I thought there might be a conflict between the various different Java packages I installed (as I installed several different ones in attempt to get the firefox plugin working until I found the ones mentioned further up on this thread).  So, I uninstalled everything and then just had icedtea-java7, but that still hasn't fixed the problem.

Any ideas?  I am running a Thinkpad laptop Ubuntu 7.10 amd64 (Intel Core 2 Duo).  All websites work like a charm on my other laptop (Kubuntu 7.04, i386) so it's not strictly the website.  Is there any way I can see how far the loading gets until it fails to initialize so as to get a better idea what's going on?

I look forward to hearing your input.

---

### Post by lns on 2007-11-16
I can also verify that only adding the 'doko' repositories (and update-java-alternatives) will get Java browser tests to return positive results.

Can anyone verify the stability of the 'doko' repository iced-tea java package/broswer plugins? I am going to use this at 6 elementary schools as it is (currently) the only functional way to get FF64 going with Java. 

Hopefully the changes will get merged with the main repos soon.

Thanks for everyone's help and collaboration on this!

- Jordan

---

### Post by tinycamp on 2007-11-16
it works!!!!

this is what i did:

close firefox....

at /etc/apt/sources.list

```
# iced-tea updates
deb http://people.ubuntu.com/~doko/ubuntu/ gutsy/
deb-src http://people.ubuntu.com/~doko/ubuntu/ gutsy/
```


then:

```
sudo aptitude update
sudo aptitude install gcjwebplugin icedtea-java7-plugin
```

finally:

```

mkdir /home/tinycamp/.mozilla/plugins
cd /home/tinycamp/.mozilla/plugins
ln -s /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so 

```

---

### Post by jw5801 on 2007-11-17
Beautiful! Thanks tinycamp. The soft link was what I needed. Any idea why the package doesn't create this itself?

---

### Post by dralokyn on 2007-11-17
i am using an amd64 x2, gutsy 64, and firefox64 2.0.0.8. with icedtea java, i could see most sites, but that wasn't acceptable to me, so i used synaptic, organized by status, and checked 'Not Installed (residual config)' where i found i had config files for three other java versions. i removed those. iced tea still only worked for some sites. i decided to give blackdown a try, as i'd read that some others had success with it. i used synaptic to remove the icedtea packages, marking remove completely so as to remove all config files. on first install, blackdown didn't work for any sites, so i double checked my symbolic links. 'ls' showed that they were unbroken, but i removed the links from three places, and manually replaced them like so:
```
sudo ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so /etc/alternatives/
sudo ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so /usr/lib/mozilla/plugins
sudo ln -s /usr/lib/j2se/1.4/jre/plugin/amd64/mozilla/libjavaplugin_oji.so /home/dralokyn/.mozilla/plugins

```
and now it works on all the sites i've visited. this is all it turned out i had to do to get the full use of java on my machine, so i've put what i learned from all the posts above so hopefully the next guy gets it done faster.

---

### Post by mabovo on 2007-11-19
> **jenhsun said:**
> Home banking?? Is that online banking or just an application?
If the test applet from sun works, that means it works.
It's not that way buddy !
I see a lot of placebo posts in this thread but there is a misunderstanding here.
If testing java works doesn't mean the java applet also works too.
For instance, in home banking You get a grey box instead of a virtual keyboard that is possible to control the colour tonality  or brigthness.

---

### Post by mabovo on 2007-11-19
> **tinycamp said:**
> it works!!!!

this is what i did:

close firefox....

at /etc/apt/sources.list

```
# iced-tea updates
deb http://people.ubuntu.com/~doko/ubuntu/ gutsy/
deb-src http://people.ubuntu.com/~doko/ubuntu/ gutsy/
```


then:

```
sudo aptitude update
sudo aptitude install gcjwebplugin icedtea-java7-plugin
```

finally:

```

mkdir /home/tinycamp/.mozilla/plugins
cd /home/tinycamp/.mozilla/plugins
ln -s /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/gcjwebplugin.so 

```

felipe@felipe-desktop:~$ sudo aptitude install gcjwebplugin icedtea-java7-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  icedtea-java7-plugin 
The following packages are unused and will be REMOVED:
  liblzo1 
The following packages have been automatically kept back:
  monodoc-manual 
The following NEW packages will be automatically installed:
  cacao classpath classpath-common classpath-gtkpeer 
The following packages have been kept back:
  acpi-support x11-common xbase-clients xorg xserver-xorg xserver-xorg-core 
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-kbd 
  xserver-xorg-input-mouse xserver-xorg-input-synaptics 
  xserver-xorg-video-all xserver-xorg-video-apm xserver-xorg-video-ark 
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus 
  xserver-xorg-video-cyrix xserver-xorg-video-dummy 
  xserver-xorg-video-fbdev xserver-xorg-video-glint xserver-xorg-video-i128 
  xserver-xorg-video-i810 xserver-xorg-video-intel xserver-xorg-video-mga 
  xserver-xorg-video-neomagic xserver-xorg-video-nv 
  xserver-xorg-video-rendition xserver-xorg-video-s3 
  xserver-xorg-video-s3virge xserver-xorg-video-savage 
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis 
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga 
  xserver-xorg-video-trident xserver-xorg-video-tseng 
  xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vga 
  xserver-xorg-video-via xserver-xorg-video-vmware 
  xserver-xorg-video-voodoo xsltproc xutils 
The following NEW packages will be installed:
  cacao classpath classpath-common classpath-gtkpeer gcjwebplugin 
0 packages upgraded, 6 newly installed, 1 to remove and 47 not upgraded.
Need to get 9731kB of archives. After unpacking 12.1MB will be used.
The following packages have unmet dependencies:
  icedtea-java7-plugin: Depends: icedtea-java7-jre (= 7~b22-1.5~20071018-0ubuntu2) but 7~b22-1.5~20071018-0ubuntu3 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
icedtea-java7-plugin [Not Installed]

Score is -9879

Accept this solution? [Y/n/q/?]

---

### Post by mabovo on 2007-11-19
More than ten years struggling in Linux and all the time I stumbled at the java runtime fighting against Firefox, Opera, Netscape, Sun, Blackdown, etc.
 Here is an interesting history:

[http://www.quirksmode.org/oddsandends/history_js_2000.html](http://www.quirksmode.org/oddsandends/history_js_2000.html)

---

### Post by jw5801 on 2007-11-19
> **mabovo said:**
> felipe@felipe-desktop:~$ sudo aptitude install gcjwebplugin icedtea-java7-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  icedtea-java7-plugin 
The following packages are unused and will be REMOVED:
  liblzo1 
The following packages have been automatically kept back:
  monodoc-manual 
The following NEW packages will be automatically installed:
  cacao classpath classpath-common classpath-gtkpeer 
The following packages have been kept back:
  acpi-support x11-common xbase-clients xorg xserver-xorg xserver-xorg-core 
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-kbd 
  xserver-xorg-input-mouse xserver-xorg-input-synaptics 
  xserver-xorg-video-all xserver-xorg-video-apm xserver-xorg-video-ark 
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus 
  xserver-xorg-video-cyrix xserver-xorg-video-dummy 
  xserver-xorg-video-fbdev xserver-xorg-video-glint xserver-xorg-video-i128 
  xserver-xorg-video-i810 xserver-xorg-video-intel xserver-xorg-video-mga 
  xserver-xorg-video-neomagic xserver-xorg-video-nv 
  xserver-xorg-video-rendition xserver-xorg-video-s3 
  xserver-xorg-video-s3virge xserver-xorg-video-savage 
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis 
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga 
  xserver-xorg-video-trident xserver-xorg-video-tseng 
  xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vga 
  xserver-xorg-video-via xserver-xorg-video-vmware 
  xserver-xorg-video-voodoo xsltproc xutils 
The following NEW packages will be installed:
  cacao classpath classpath-common classpath-gtkpeer gcjwebplugin 
0 packages upgraded, 6 newly installed, 1 to remove and 47 not upgraded.
Need to get 9731kB of archives. After unpacking 12.1MB will be used.
The following packages have unmet dependencies:
  icedtea-java7-plugin: Depends: icedtea-java7-jre (= 7~b22-1.5~20071018-0ubuntu2) but 7~b22-1.5~20071018-0ubuntu3 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
icedtea-java7-plugin [Not Installed]

Score is -9879

Accept this solution? [Y/n/q/?]

The commands listed in the post you quoted are good, but something has borked apt on your machine. You already have the jre installed from another source it would appear. Try removing it and then installing the plugin:```
sudo apt-get remove icedtea-java7-jre
sudo apt-get install icedtea-java7-plugin
```etc etc.

There are also quite a few packages there waiting for you to run an upgrade! So you probably want to run "sudo apt-get upgrade" as well.

---

### Post by ruru on 2007-11-21
> Uninstall the icedtea packages and install the sun-java6 packages. If it works, then there's still some issues with icedtea that have to be resolved. I've noticed that there are issues with icedtea still popping up in the fedora forums as well.

Please also note that if you do revert back to sun-java6, you'll lose the firefox plugin.


There's no reason not to have ***both*** java versions running...
I use sun-java6 (default) for applications, sun-java5 for development (compatibility with mac!) and  icetea-java7 just for the firefox plugin.
All are 64-bit and all play just nicely with each other.

---

### Post by mabovo on 2007-11-21
felipe@felipe-desktop:~$ sudo apt-get remove icedtea-java7-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  icedtea-java7-bin icedtea-java7-jre
0 upgraded, 0 newly installed, 2 to remove and 47 not upgraded.
Need to get 0B of archives.
After unpacking 78.3MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 124928 files and directories currently installed.)
Removing icedtea-java7-bin ...
Removing icedtea-java7-jre ...
felipe@felipe-desktop:~$ sudo apt-get install icedtea-java7-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  icedtea-java7-plugin: Depends: icedtea-java7-jre (= 7~b22-1.5~20071018-0ubuntu2) but it is not going to be installed
E: Broken packages
felipe@felipe-desktop:~$

---

### Post by angryfirelord on 2007-11-21
> There's no reason not to have both java versions running...
I use sun-java6 (default) for applications, sun-java5 for development (compatibility with mac!) and icetea-java7 just for the firefox plugin.
All are 64-bit and all play just nicely with each other.
Makes sense, although how would you be able to switch between the sun-java6 & sun-java5 when needed?
> elipe@felipe-desktop:~$ sudo apt-get remove icedtea-java7-jre
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
icedtea-java7-bin icedtea-java7-jre
0 upgraded, 0 newly installed, 2 to remove and 47 not upgraded.
Need to get 0B of archives.
After unpacking 78.3MB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 124928 files and directories currently installed.)
Removing icedtea-java7-bin ...
Removing icedtea-java7-jre ...
felipe@felipe-desktop:~$ sudo apt-get install icedtea-java7-plugin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
icedtea-java7-plugin: Depends: icedtea-java7-jre (= 7~b22-1.5~20071018-0ubuntu2) but it is not going to be installed
E: Broken packages
felipe@felipe-desktop:~$
Make sure that icedtea-updates repo is in your system. If it is, then I would wait until it gets resolved (just do an apt-get update once in a while). Bascially, it's telling you that the icedtea-java7-jre package is missing (someone probably forgot to upload it).

---

### Post by ruru on 2007-11-23
> 
Makes sense, although how would you be able to switch between the sun-java6 & sun-java5 when needed?


Just call the correct java executable when you start the program. 
i.e. a launcher that runs '/path-to-java5/java -jar jar_file_name'

The icetea version on my machine is only there for the plugin.

---

### Post by angryfirelord on 2007-11-23
> **ruru said:**
> Just call the correct java executable when you start the program. 
i.e. a launcher that runs '/path-to-java5/java -jar jar_file_name'

The icetea version on my machine is only there for the plugin.
Ah, I see, you explicitly called the path. I pictured you were using an IDE for whatever reason. Oh well, thanks for the tip!

---

### Post by maitrebart on 2007-11-23
> **wwright said:**
> no the pop up window opens just fine says loading, It never loads and then tells me java is not detected or configured properly. Yet everything else java I´ve had no problems with

I have exactly the same problem. As someone did, I added the doko repos and completely reinstalled IcedTea and it's still not working.

I put in attchement an output log of firefox started in safe-mode. I also put my list of java plugins listed in about : plugins.

I would add that when the pogo's game popup opens, it says "downloading..." but looking at my network monitor, nothing actually download. I have java enabled and popup blocking disabled.

I hope someone may help.

---

### Post by lns on 2007-12-03
OK - There's a lot of different people having different issues here, so **I thought I'd post a recent reply that explains EXACTLY how to get icedtea running on Gutsy 64-bit** (this assumes a FRESH INSTALL of Gutsy with no previous fiddling with Java and/or Java Firefox plugins.

1) Ok, first off, edit your /etc/apt/sources.list and add the following:

```
# iced-tea java updates
# THIS SHOULD BE REMOVED ONCED THE OFFICIAL ICED-TEA JAVA
# PACKAGES ARE STABLE AND WORKING.
deb http://people.ubuntu.com/~doko/ubuntu/ gutsy/
deb-src http://people.ubuntu.com/~doko/ubuntu/ gutsy/
```

2) Now update your apt repositories:

```
$ sudo apt-get update
```

3) Now install the icedtea Java stuff:

```
$ sudo apt-get install gcjwebplugin icedtea-java7-plugin
```

4) IF YOU DID MESS WITH JAVA BEFOREHAND, updating your Java alternatives might help:

```
$sudo update-java-alternatives -s java-7-icedtea
```

5) Test your Java plugin by visiting [http://www.javatester.org]("http://www.javatester.org") and click on the link on the page that says "Test the version of Java your browser is using".

6) If it works, re-edit your /etc/apt/sources.list file and comment out the doko repositories, so when there's an update from Canonical, they'll work instead of break your whole system:

```
# THIS SHOULD BE REMOVED ONCED THE OFFICIAL ICED-TEA JAVA
# PACKAGES ARE STABLE AND WORKING.
# deb http://people.ubuntu.com/~doko/ubuntu/ gutsy/
# deb-src http://people.ubuntu.com/~doko/ubuntu/ gutsy/
```

I just did this on a new Gutsy install (minus the update-java-alternatives) and it works fine. If it doesn't, you probably broke something while troubleshooting (or versions have changed, the doko repository is down, or little green elves are messing with your computer)

---

### Post by michael37 on 2007-12-11
> **angryfirelord said:**
> Whoa, it works! Thanks you very much! :KS

At this point, yes, but it has two featues that make 1.7 more exciting over 1.6:

-It's GPL'd. No more Sun license on Java, it's now covered under GPLv3, so this means that distros like Fedora can include it on the disc.
-It has a 64-bit plugin for Firefox. Previous versions of Java (1.6 down) didn't have this, so you'd either have to go with blackdown or gcj, both of which are buggy.

Thank you, thank you, thank you.  Initial install of icedtea-java7-plugin from universe didn't work for me -- the plugin kept crashing.  The install from people.ubuntu.com/~doko works well, although it gives a scary warning about "not for public use" from [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml))

[[IMG]http://img153.imageshack.us/img153/9304/screenshot1xh5.jpg[/IMG]](http://img153.imageshack.us/my.php?image=screenshot1xh5.jpg)

---

### Post by edv on 2007-12-22
hey. i solved the "applet not initialized" error by editing

*/etc/java-7-icedtea/security/java.policy*

and adding this line to the grant section:

*permission java.security.AllPermission;*

so it looks like:

[I]grant {
        // Allows any thread to stop itself using the java.lang.Thread.stop()
        // method that takes no argument.
        // Note that this permission is granted by default only to remain
        // backwards compatible.
        // It is strongly recommended that you either remove this permission
        // from this policy file or further restrict it to code sources
        // that you specify, because Thread.stop() is potentially unsafe.
        // See "http://java.sun.com/notes" for more information.
        permission java.security.AllPermission;
        permission java.lang.RuntimePermission "stopThread";[/I]

etc...


NOTE: This is probably a bad idea because it allows basically any applet to do anything which you don't want. Better is to add a separate section for each domain where you need to use an applet. Like:

[I]grant codeBase "http://www.mynetbankwhichusesjava.com/*" {
        permission java.security.AllPermission;
};[/I]

---

### Post by aelius on 2007-12-23
The guide previously posted by lns gets IcedTea to work. Most applets seems to work now in Firefox 64-bit.
Thanx!!!

---

### Post by kyllikki on 2008-01-19
Iced Tea works fine for me when I run the test pages although I do have the problem with the greyed out applet on a particular website.  The applet in question is the Upload Applet in Gallery2.  I am getting a java.lang.ExceptionInInitializationError.  I have read through and tried the suggestions in previous posts but still cannot get it to work.  Any advice on how to resolve this problem would be much appreciated.

---

### Post by MinceMedallion on 2008-02-04
> **skylark said:**
> I had the same problem. I fixed it by adding the unofficial iced-tea gutsy repository to my apt sources. I did this by appending the following lines to /etc/apt/sources.list (and then doing the usual update and upgrade):

```
# iced-tea updates
deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
```

I have noticed it can a while for some plugins to start though (up to 10 seconds with my setup) but at least they seem to work.

Thanks, Skylark. Followed your instructions and Hey Presto! Java is now working properly. I'm running Ubuntu 7.10 64 bit and Java was proving to be a struggle. Thanks for the help! MinceMedallion.

---

### Post by Angus77 on 2008-02-06
> I had the same problem. I fixed it by adding the unofficial iced-tea gutsy repository to my apt sources. I did this by appending the following lines to /etc/apt/sources.list (and then doing the usual update and upgrade):

Code:

# iced-tea updates
deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/

I have noticed it can a while for some plugins to start though (up to 10 seconds with my setup) but at least they seem to work.

This is what worked for me!

Thanks a lot!

---

### Post by sforces on 2008-02-22
Worked great! I've tried other suggestions and this is the first that worked finally. I'm on Gutsy and Firefox 2.0.0.12

Thank you!

---

### Post by Kivech on 2008-03-07
OMG, this is beautiful! Got it working now too!

Thanks a ton for such a clean and simple fix!

Kivech

---

### Post by aleoje on 2008-03-19
Will this solution work for non-64 bit installations? And USB Ubuntu instalations? (pendrivelinux.com). Thanks!!

---

### Post by jw5801 on 2008-03-19
Why would this solution be necessary on 32 bit installs? On a 32-bit install there is a proper sun java plugin. A USB install will also be either 32-bit or 64-bit (or powerpc, etc), so the same answer applies.

---

### Post by mohbana on 2008-03-20
why is taking so long to fix??? have they fixed this for gusty?

---

### Post by wolfchri on 2008-03-23
Hello,

Issue is solved on Hardy:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-restricted-extras/+bug/205282](https://bugs.launchpad.net/ubuntu/+source/ubuntu-restricted-extras/+bug/205282)

--> just install ubuntu-restricted-extras, which brings you a working java plugin for firefox.

---

### Post by JEdwardP on 2008-04-26
Now that I've upgraded from Gutsy64 to Hardy64, Java no longer works.

I did install ubuntu-restrcted-extras, but any page I visit that uses java still claims I'm missing the JRE plug-in.

---

### Post by QCompson on 2008-04-26
> **JEdwardP said:**
> Now that I've upgraded from Gutsy64 to Hardy64, Java no longer works.

I did install ubuntu-restrcted-extras, but any page I visit that uses java still claims I'm missing the JRE plug-in.

Similar problem here.  Java applets are not working for me in Hardy-64.  I have ubuntu-restricted extras, icedtea and its plugin, and java jre from sun installed.  Everything worked fine in Gutsy-64.

---

### Post by jw5801 on 2008-04-26
> **QCompson said:**
> Similar problem here.  Java applets are not working for me in Hardy-64.  I have ubuntu-restricted extras, icedtea and its plugin, and java jre from sun installed.  Everything worked fine in Gutsy-64.

You shouldn't need anything other than ubuntu-restricted-extras. In fact, installing things from this repository is likely to break things in Hardy. ubuntu-restricted-extras includes the flash plugin, java plugin and a bunch of other things for 64-bit (as well as for 32-bit). Everything should work fine without any external repositories.

---

### Post by JEdwardP on 2008-04-26
I anticipated some sort of conflict, so I uninstalled Icedtea when I installed ubuntu-restricted-extras. This makes no difference; java still doesn't work.

---

### Post by sadohert on 2008-04-30
Well... HUGE thanks to all the helpful people on this thread.  I tried to get it sorted out, but no matter what I did I could not get the two applets I need to work (one was for the government of canada epass service, and the other was the gotomypc.com universal viewer applet).  The test applet worked...and although I didn't get the applets working, tweaking these changes seemed to be changing things up....I learned a bunch about how different java versions manage to operate beside each other w.r.t. the browser...

But... alas... I needed to stop f'ing around with my system and just have it work.  So, I 32bit the bullet and installed firefox 32. [HERE]("http://ubuntuforums.org/showthread.php?t=202537&highlight=Gutsy")

I hated the thought of NOT USING ALL MY BITS!!! :lolflag:...but when it came down to it I'm not sure I could really describe the negative impacts of 32 bit for me.  AND an added bonus is that I can now install the google toolbar in firefox, and go back to using my google bookmarks.

I'll keep this thread subscribed in case I hear of anyone having better luck.

Good luck to you.

Stu

---

### Post by verbal.kint on 2008-05-27
what exactly do you lose when you switch back to Firefox 32bit?

does anyone know when the problem will be solved correctly instead of these workarounds. I'm still struggling as it seems alot of people are

---

