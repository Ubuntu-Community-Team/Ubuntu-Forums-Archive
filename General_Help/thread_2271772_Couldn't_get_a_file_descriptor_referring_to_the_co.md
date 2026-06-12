---
title: "Couldn't get a file descriptor referring to the console"
date: 2015-04-01
forum: General Help
---

### Post by zeroo on 2015-04-01
Hello,

I'm trying to edit “~/.profile” to set up set up some persistent environmental variables for a program.  The part where “.profile” complains is when I try to run [COLOR="#FF0000"]loadkeys[/COLOR].  I realize that the [COLOR="#B22222"]loadkeys[/COLOR] command needs to be run in root, which I think is the problem.  I have minimum security risks on this computer as it will be an offline computer for a company running a database.  

I've tried:  [COLOR="#B22222"][COLOR="#B22222"]echo $PASSWORD | sudo -S loadkeys <directory of file>[/COLOR][/COLOR]
		-where the [COLOR="#0000CD"]PASSWORD[/COLOR] variable is set as the root password but that still brings up the same error.. 

Is there a way to run sudo commands within a bash script?  Or would I need to remove sudo password requirements altogether.  Again, security is a minimal issue on this computer, after I am done programming the software, it will be used only in offline mode.
  

Thanks

---

### Post by zeroo on 2015-04-01
I figured it out. 

All I did was create a separate script, give that script permission to run without root password in visudo, and then tell [COLOR="#B22222"]"~/.profile"[/COLOR] to run that script.  

The information was taken from: [http://askubuntu.com/questions/155791/how-do-i-sudo-a-command-in-a-script-without-being-asked-for-a-password](http://askubuntu.com/questions/155791/how-do-i-sudo-a-command-in-a-script-without-being-asked-for-a-password)

---

