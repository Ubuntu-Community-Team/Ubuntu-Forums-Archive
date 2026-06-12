---
title: "Help APache Tomcat Wont Do Anything"
date: 2007-07-23
forum: General Help
---

### Post by netvampire on 2007-07-23
HELP PLEASE.

I have apache tomcat 6.0.13, and every time i run startup.sh from the /bin folder this happens;

```

mo@kismet:~/WebDevelopment/apache-tomcat-6.0.13/bin$ ./startup.sh
Using CATALINA_BASE:   /home/mo/WebDevelopment/apache-tomcat-6.0.13
Using CATALINA_HOME:   /home/mo/WebDevelopment/apache-tomcat-6.0.13
Using CATALINA_TMPDIR: /home/mo/WebDevelopment/apache-tomcat-6.0.13/temp
Using JRE_HOME:       /opt/jdk1.5.0_12
mo@kismet:~/WebDevelopment/apache-tomcat-6.0.13/bin$

```

After that, NOTHING. it seems that the serer begins to start, but exits somewhere in the middle. On one thread I read that I should try installing apache2. I did this, however I had not done anything to 'start it up'. I assume it is done in the background. 

Can anyone help me with this. I really need  tomcat.

Thanks.

---

### Post by netvampire on 2007-07-23
bump

---

### Post by sgordon on 2007-07-27
Hard to see what is wrong with so little response you are seeing!

I suggest that you start tomcat in this fashion. This will output to the console. Perhaps paste the output from that here and we can have a look?

[FONT="Courier New"]$ ./catalina.sh run[/FONT]

  SG

---

### Post by zanglang on 2007-07-27
I recall Tomcat forks to the background when it runs... Check if it's running with
> ps ax | grep tomcat
Have you checked the logs (catalina.out and so on) and see if it's failing with errors?

Alternatively, you can install the tomcat5.5 package, which although is bundled oddly and needs a bit of mucking around to get it to run after install, but works brilliantly afterwards...

---

