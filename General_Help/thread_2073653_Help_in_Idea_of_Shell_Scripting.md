---
title: "Help in Idea of Shell Scripting"
date: 2012-10-20
forum: General Help
---

### Post by Mohan1289 on 2012-10-20
Hi friends

i wanna write a script which helps my friends 

but i am getting lot of complications though to me it looks little easy but not

in our company my colleges are developing  various applications and deploying them Manually

1. First they are creating a **project.war.zip** file in windows using NET BEANS

2. Then they are Deploying them in CENT OS using FileZilla

3.Then they Move **.war** file to **/root/jboss-4.0.5GA/server/default/deploy**

4. Service jboss stop and check for  processes using ps ax | grep jboss 

5. if it shows more than one process then kill the remaining processes except jboss

6. service start jboss

7. serverlogs:
tail -f /root/jboss-4.0.5GA/server/default/log/serverlog[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]


8. import 
what i wanna do is
if i write a script and run it after downloading the package it should do all the above processes automatically no manual work should be done..

How can i do this?? any suggestions??

---

