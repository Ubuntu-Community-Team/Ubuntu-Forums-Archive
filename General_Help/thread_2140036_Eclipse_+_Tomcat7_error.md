---
title: "Eclipse + Tomcat7 error"
date: 2013-04-28
forum: General Help
---

### Post by cpu2007 on 2013-04-28
Hi

I'm having problem trying to run tomcat7 in eclipse.

I have tried a few solutions but none of the worked.

In eclipse when I set a new server using the wizard option, I chose the tomcat7 server which is situation in /usr/share/tomcat7

I went to properties and switched the location which has then allowed me to change one setting option in tomcat server (Use tomcat installation - takes control of tomcat installation),this is disabled if the previous step is not followed.

After starting the server, I get the following error:

Publishing the configuration...
Error copying file to /usr/share/tomcat7/backup/catalina.policy: /usr/share/tomcat7/backup/catalina.policy (No such file or directory)


The error lenght is longer than what is shown above but is about files/directories missing.

Can someone exaplain me why I'm getting this error?

Thank you

---

### Post by cpu2007 on 2013-04-29
What I did is to copy files from the conf folder, create a backup folder and put the files in that folder as this is the directory that tomcat is looking for in eclipse.
Once I done this, the error regarding "publishing the configuration...." was gone.
However now when I go in localhost:8080, I see black page as opposed to a 404 error.
In the console there's only one error about a log file but not sure what is wrong.

any advice?

---

### Post by cpu2007 on 2013-05-01
does anyone know why is this happening?:confused:

---

### Post by cpu2007 on 2013-05-03
I have managed to make it work. 
  
 I'm going to post here what I've done so other can get some help out of it. 
  
 Apparently some folders were missing from my tomcat7 application so  instead of installing it from the command line,I've unistalled it and  downloaded a .gz version from the tomcat website. 
  
 After doing this, I extracted the tomcat7 folder and moved it to /usr/share/ - called it tomcat7 
 inside the folder, the backup folder is missing and when setting up  tomca in eclipse it throughs an error because of the missing folder. To  solve this I created the "backup" folder and copied all the files from  the "conf" folder to the newly created one. 
  
 I set the settings in eclipse by going in the server  properties>pressing "switch location" and this would change the  location from "workspace" to the location of tomcat files. 
 Lastly, in eclipse>tomcat server in the configuration area I  changed the option to "Use Tomcat installation, takes control of tomcat  installation".  
  
 Also, go to the xml file tomcat-user and set manager-gui and other  username and passwords(you can find the configuration online) and this  will allow you to access the server-status,manager app etc. 
  
 Hope this helps

---

