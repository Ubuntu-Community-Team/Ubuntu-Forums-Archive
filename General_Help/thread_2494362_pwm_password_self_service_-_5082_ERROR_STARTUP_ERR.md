---
title: "pwm password self service - 5082 ERROR_STARTUP_ERROR"
date: 2024-01-14
forum: General Help
---

### Post by robertkwild on 2024-01-14
hi all,


so i have followed the how to guide here


[https://github.com/pwm-project/pwm/wiki/Installation-on-Ubuntu-Server-20.04-LTS-(Draft)](https://github.com/pwm-project/pwm/wiki/Installation-on-Ubuntu-Server-20.04-LTS-(Draft))


only difference is im doing the pwm install on ubuntu 22 LTS


i get this error on the web portal



 5082 ERROR_STARTUP_ERROR (applicationPath /home/pwm01/pwm-data does not exist) 



as you can see ive added my path to all the files in the documentation, il show you


ls -lah /home/pwm01/pwm-data/
total 8.0K
drwxrwxrwx 2 tomcat tomcat 4.0K Jan 12 17:22 .
drwxr-x--- 5 pwm01  pwm01  4.0K Jan 12 17:22 ..
root@pwm01:~#


ive chmoded it 777 just for testing, il redo once i get it working


in "/lib/systemd/system/tomcat9.service"


under service config


Environment="PWM_APPLICATIONPATH=/home/pwm01/pwm-data/"


under security


ReadWritePaths=/home/pwm01/pwm-data


in "/etc/default/tomcat9"


PWM_APPLICATIONPATH=/home/pwm01/pwm-data
PASSWORD_APPLICATIONPATH=/home/pwm01/pwm-data


and last in "/var/lib/tomcat9/webapps/pwm/WEB-INF/web.xml"


<param-name>applicationPath</param-name>
        <param-value>/home/pwm01/pwm-data</param-value>


i have then reloaded restarted everything


systemctl daemon-reload
systemctl enable --now tomcat9
service tomcat9 restart


im root so i dont need sudo but when i go to my web portal i get the 



5082 ERROR_STARTUP_ERROR


any help in this, i would really appreciate it
  


thanks,
rob

---

