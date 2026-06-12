---
title: "Strange behavior of pidof function"
date: 2018-05-24
forum: General Help
---

### Post by poliman-pl on 2018-05-24
I  have a script which checks that some node server process is running or  not. I use pidof function, i.e. ```
pidof dziup-server-prod.js
```  As you can see there is full server name with file extension. But for  some names I have to use shorter name, because pidof does not find the  process. I have this issue with, i.e. ```
quiz3m-server-test.js
```  Pidof finds the process when I put as parameter shorter name like  ```
quiz3m-server-tes
``` Below you can see the examples:
```
root@s1:~/skrypty# pidof quiz3m-server-test.js
root@s1:~/skrypty# pidof quiz3m-server-test.j
root@s1:~/skrypty# pidof quiz3m-server-test
root@s1:~/skrypty# pidof quiz3m-server-tes
3945
root@s1:~/skrypty# pidof dziup-server-prod.js
30636
root@s1:~/skrypty# pidof quiz3m-server-prod.js
11807

```


I don't understand why pidof works this way. I attached the screenshots with addtitional informations related with mentioned problem.


PS
Path and name of each server file mentioned above:
/var/www/clients/client4/web4/web/tquiz3m/quiz3m-server-test.js
/var/www/clients/client30/web88/web/dziup-server-prod.js

---

### Post by nlee2 on 2018-05-24
What is the output of

ps -ef | grep quiz3m-server-tes
pidof -x /var/www/clients/client4/web4/web/tquiz3m/quiz3m-server-test.js

---

### Post by poliman-pl on 2018-05-28
Sorry for long break from response - vacation. Here is the result:
```

root@s1:~# ps -ef | grep quiz3m-server-tes
root     12121  1865  0 May23 ?        00:04:16 node /var/www/clients/client4/web4/web/tquiz3m/quiz3m-server-tes
root     17159 17117  0 07:28 pts/0    00:00:00 grep --color=auto quiz3m-server-tes
root@s1:~# pidof -x /var/www/clients/client4/web4/web/tquiz3m/quiz3m-server-test.js
root@s1:~#

```

PS
I thought that this behavior is produced by too long path/ too much letters in path.

---

