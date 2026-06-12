---
title: "Bash scrip which ping several servers and execute command"
date: 2014-07-30
forum: General Help
---

### Post by vinsbg on 2014-07-30
Hello,

So far I have this script which pings 7 servers and execute an command if the server is alive. What I need is to put parameter which will change in the command according to server. For example:
>  
ping SERVER 1 -> response with OK -> execute command /snmptrap -v 2c -c public  **server_1 param_[SIZE=5]1[/SIZE]** ....
ping SERVER 2 -> response with OK -> execute command /snmptrap -v 2c -c public  **server_2 param_[SIZE=5]2[/SIZE]** ....
ping SERVER 3 -> response with OK -> execute command /snmptrap -v 2c -c public  **server_3 param_[SIZE=5]3[/SIZE]** ....

My problem is how to put in array those parameters ( 1; 2; 3; ) and in the command call them according to server which is alive. If server 1 is alive execute command with parameter 1 ... server 2 with parameter 2 and so on. 

Here is the script that I ping the servers.
```

#!/bin/bash
servers=( "ip_serv_1" "ip_serv_2" "ip_serv_3" )

for i in "${servers[@]}"; do
    ping -c 1 $i > /dev/null && /snmptrap -v 2c -c public ...
done

```

EDIT:

Can I do something like this?
```

#!/bin/bash
servers=( "ip_serv_1" "ip_serv_2" "ip_serv_3" )
**cmd=("1" "2" "3" "4")**

for i in "${servers[@]}"; do
    ping -c 1 $i > /dev/null && /snmptrap -v 2c -c public ... **$cmd...**
done

```
But I guess if some host is down will mess the commands like this? SOmehow each $param must be assigned to corresponded host..

---

### Post by HermanAB on 2014-07-30
Google for Parallel SSH.

---

### Post by vinsbg on 2014-07-30
> **HermanAB said:**
> Google for Parallel SSH.
Thank you for replay!
I don't understand why I need this. I don't want to execute command from script on remote host. I will execute it on local.

Edit: I'm not shell-bash-script-guru and just starting to learn. That is why I dont understand some things.

---

