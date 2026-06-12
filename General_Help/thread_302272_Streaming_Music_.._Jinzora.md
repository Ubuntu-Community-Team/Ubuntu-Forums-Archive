---
title: "Streaming Music .. Jinzora"
date: 2006-11-18
forum: General Help
---

### Post by habtish on 2006-11-18
I was reading a thread [http://www.ubuntuforums.org/showthread.php?t=266702]("http://www.ubuntuforums.org/showthread.php?t=266702")  about accessing local music remotely and streaming music services and came across "Jinzora" 
The installation is a web based install and i am getting stuck on where it checks for system requirements...
```
  	   	
Setting 	             Actual 	         Recommend
max_execution_time: 	    30                     300+
	
memory_limit: 	            18M                     32M+
	
post_max_size: 	            8M                      32M+
	
upload_max_filesize: 	    2M                     32M+

```

I went to /etc/php4/apache2/php.ini and changed these settings to meet the requirement. When I try to "recheck" these requirements, I keep on getting the same errors and it is showing me that my changes have not taken effect. Going back into the php.ini file shows that I have made those changes and saved them. 

Has anyone tried to install this app.. any help is appreciated

---

### Post by keeb on 2006-11-21
Make sure to restart apache.

---

### Post by stokedfish on 2007-03-13
Yeah, save your changes, then restart apache!

---

