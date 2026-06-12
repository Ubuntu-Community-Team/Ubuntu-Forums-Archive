---
title: "[SOLVED] change Tomcat 5.5 webapp folder"
date: 2007-12-01
forum: General Help
---

### Post by myharshdesigner on 2007-12-01
i want to change **webapp** folder of tomcat to **/home/username/web/tomcat/**


any one know to do that ?

in which file i have to change the path ?

---

### Post by myharshdesigner on 2007-12-01
any one can able to tell me ?

---

### Post by sgordon on 2007-12-03
Seems a bit different on a Feisty box I'm playing with, but the usual would be to change the file:

/etc/tomcat5.5/server.xml

the section to change is:

```
      <Host name="localhost" appBase="webapps"
       unpackWARs="true" autoDeploy="true"
       xmlValidation="false" xmlNamespaceAware="false">

```

Change appBase attribute to the path you want. Ensure the tomcat55 user has permissions to read AND write to that folder so that it can expand the WAR files. (Or change unpackWARs to false if you aren't keen on this)

I think that's all, can't try it out on my rig as yet. Let me know how it goes.

  Si

---

### Post by myharshdesigner on 2007-12-03
how to restart tomcat ?

---

### Post by myharshdesigner on 2007-12-03
i have got this from 

** /usr/share/tomcat5.5-webapps/ROOT.xml**

> 

<Context path="/" docBase="/usr/share/tomcat5.5-webapps/ROOT" 
   debug="0" privileged="true" allowLinking="true">
</Context>


when i change this to this :-
> 
<Context path="/" docBase="/home/harsh/web/tomcat" 
   debug="0" privileged="true" allowLinking="true">
</Context>


then i will got an error :-

> 
HTTP Status 404 - /

type Status report

message /

description The requested resource (/) is not available.
Apache Tomcat/5.5



why ?

and i wnt to set my this path as workdir

**/home/harsh/web/tomcat**

how to do that ?

---

### Post by myharshdesigner on 2007-12-04
hello any one know ho to solve this problem ?

---

### Post by myharshdesigner on 2007-12-05
any one can tell me what's the problem ?

---

### Post by jespdj on 2007-12-06
Do you have an index.html or any web applications in /home/harsh/web/tomcat ? If not, then you'll get a 404 error (because Tomcat can't find a page to display).

You should really try to read and understand the Tomcat documentation:
[http://tomcat.apache.org/tomcat-5.5-doc/index.html](http://tomcat.apache.org/tomcat-5.5-doc/index.html)

---

