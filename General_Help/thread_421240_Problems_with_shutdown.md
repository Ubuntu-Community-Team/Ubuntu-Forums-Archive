---
title: "Problems with shutdown"
date: 2007-04-24
forum: General Help
---

### Post by marbles on 2007-04-24
Hi, 

I have a problem with my shutdown. When I click on "System" / "Quit" the dialog for shuting down does not come up, instead the task bar is not responding to my mouse any more. 
I put a shutdown button on my taskbar but with the same results, if I hit it the task bars freeze. 
Everything still works. Via the console I can shutdown: sudo shutdown -h now. 

I had the Problem under Dapper and after the Feisty upgrade it is still there? 

Any ideas? 

Thanks

---

### Post by dannyboy79 on 2007-04-24
so are you saying that you added a new item the panel and used the command

sudo shutdown -h now

and that results in a freeze as well? hum, have you checked out some of the log files within /var/log? like syslog or similar? sounds like maybe an issue with the panel? maybe try removing the panel and adding another. I don't know what to suggest, sorry. do you use noapic or nolapic as boot options? what does 

lspci -v 

show?

---

