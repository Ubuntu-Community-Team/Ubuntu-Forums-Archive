---
title: "Syntax of iptables rule to send all packets to a sub chain"
date: 2015-03-01
forum: General Help
---

### Post by HereInOz on 2015-03-01
Hi All,

I would like to set up rules in the INPUT chain of iptables so that when any packet arrives at the firewall, it is directed to a sub chain, and then returned to the INPUT chain if there is no match.

I have the sub chain in place - I just can't seem to get the firewall to get out of the INPUT chain to the sub chain, have a look and then back again.

Can anyone assist?  I too will continue browsing the web for a solution.  Hope you can help.

Cheers,

Alan

---

### Post by HereInOz on 2015-03-03
This all started on an Ubuntu Server in the "Perfect Server" configuration from howtoforge.com.  It is running fail2ban and IspConfig3, among others.  I found that fail2ban was not working, and then realised that the ufw firewall was not running.  I then started the firewall and that then blocked everything.  

I checked the firewall configuration:  sudo iptables -L | more 
 
I added an "ACCEPT all" rule to the bottome of the INPUT chain:  sudo iptables -I INPUT {line number required to put it at the bottome of the INPUT chain} -j ACCEPT

Everything was then accepted again, including the IP addresses added to the fail2ban sub chains by the fail2ban software.  This is not how it is supposed to go :-(

In the end, I created four new fail2ban sub chain rules on lines 1 - 4 of the INPUT chain:  sudo iptables -I INPUT -p tcp -j {the name of the fail2ban subchain you want to go to}

and then deleted the 4 original fail2ban rules which were now on lines 5 -8:  sudo iptables -D INPUT {the number of the line you want to delete}

That seemed to work fine, until I did an update of something (it was late and I didn't look) which reset the firewall to the original settings and I had to do it again.  Avoiding this aspect is a work in progress.

---

### Post by kjohri on 2015-03-04
Look at the firewall script in this post, [iptables]("http://www.softprayog.in/tutorials/iptables").

---

### Post by JKyleOKC on 2015-03-04
> **HereInOz said:**
> In the end, I created four new fail2ban sub chain rules on lines 1 - 4 of the INPUT chain:  sudo iptables -I INPUT -p tcp -j {the name of the fail2ban subchain you want to go to}

and then deleted the 4 original fail2ban rules which were now on lines 5 -8:  sudo iptables -D INPUT {the number of the line you want to delete}

That seemed to work fine, until I did an update of something (it was late and I didn't look) which reset the firewall to the original settings and I had to do it again.  Avoiding this aspect is a work in progress.You should not have needed to replace the fail2ban rules near the start of the INPUT chain; the fail2ban service adds them automatically during its startup code, and removes them when the service stops during shutdown.

If you do a system update that requires a reboot, it's best to manually stop the fail2ban service before rebooting, to make sure that the Iptables rule set returns to its default condition so that the consequent startup doesn't confuse fail2ban's actions. That just might have been the cause of your original problem.

As a general answer to your first question, simply jumping to a subchain achieves your desired action. Upon reaching the end of the subchain without going elsewhere, control automatically returns to the rule immediately following the original jump. Adding a jump to ACCEPT at the end of the INPUT chain simply does the same thing as setting the chain's policy to ACCEPT; it ought not have had any effect on subchain action. Perhaps it got put at the top of the chain, rather than at its end. I use -A to append to the end of a chain, and -I to put a new rule at its head.

Hope this helps a bit!

---

