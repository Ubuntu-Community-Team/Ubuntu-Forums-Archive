---
title: "how do i get to the Tomcat gui?"
date: 2008-03-11
forum: General Help
---

### Post by thepiston on 2008-03-11
I'm a noob, but managed to get my LAMP server running with all the bells and whistles thus far.  I followed a tutorial and set up Tomcat.  Isn't there a web GUI?  How do I get to it?

---

### Post by OffAxis on 2008-03-11
what version of tomcat did you install?

If you installed 4.1 just navigate to 
[http://localhost:8080/admin](http://localhost:8080/admin)
otherwise read on...

This is straight out of the tomcat wiki found here: 
[http://wiki.apache.org/tomcat/HowTo#head-f50555909547d981d0e2b030323632b26047013e]("http://wiki.apache.org/tomcat/HowTo#head-f50555909547d981d0e2b030323632b26047013e")

> How do I install the Administration web app?

If you install Tomcat 5.5 binaries, the Administration web app is not bundled with it; this describes how to add the Administration web app to your Tomcat 5.5 installation. (Tomcat 4.1 comes with the Administration web app as part of the binary).

The following refers to a Tomcat 5.5 set up on Windows 2000, so your path names will be different on *nix platforms. In this example, Tomcat 5.5.17 in installed in c:\Program Files\Apache Software Foundation\Tomcat 5.5 (this is my CATALINA_HOME).

   1.

      Unzip or untar (be careful to use GNU tar) the file containing the administration web app files (eg. apache-tomcat-5.5.17-admin.zip) to a temporary directory, eg. c:\temp.
   2.

      Copy c:\temp\apache-tomcat-5.5.17\conf\Catalina\localhost\admin.xml to the directory c:\Program Files\Apache Software Foundation\Tomcat 5.5\conf\Catalina\localhost.
   3.

      Copy the entire directory tree c:\temp\apache-tomcat-5.5.17\server\webapps\admin

to the directory c:\Program Files\Apache Software Foundation\Tomcat 5.5\server\webapps. This is an overlay, so \server\webapps is just pointing you to the \server\webapps, and the admin directory with its contents will be the only thing you see added there.

   1.

      Add a line to your c:\Program Files\Apache Software Foundation\Tomcat 5.5\conf\tomcat-users.xml file so that you have a user who has admin role. For example, add this line just before the last line (containing </tomcat-users>) of the file:
          *

            <user username="admin" password="makesomethingup" roles="admin,manager"/>
   2.

      Restart Tomcat.
   3.

      Now when you visit [WWW] [http://localhost:8080/admin](http://localhost:8080/admin) you should see a page that asks for a user name and password. If you still see the "no longer loaded" error message in your browser, you must either force a full reload of the web page (in Firefox, hold down Shift key while clicking on the Reload button) or just restart your browser completely.


---

### Post by thepiston on 2008-03-11
Thanks, but I installed version 6... I dont' see anything running on port 8080 - how do I find out if I have it starting at boot?

I have tried both ports 8080 and 8180 and nothing is there... 

Do I need to delete normal Apache?  I'm so confused

**EDIT**
I used webmin to show me all the processes and I dont' see Tomcat running... I know I added the code to make it start and stop like the tutorial said... I've checked that twice.

---

