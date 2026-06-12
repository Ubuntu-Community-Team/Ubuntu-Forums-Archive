---
title: "Nagios Postfix sendmail error"
date: 2016-02-18
forum: General Help
---

### Post by mike405 on 2016-02-18
Hello all first time user here,

let me set the scenario that has brought me here seeking assistance.

I have installed Ubuntu 14.04.3 LTS Trusty as a vm.  After package updates, upgrades I installed postfix.  I configured postfix to be an smtp relay using a gmail account.  I confirmed functionality with test emails and log reviews.  I then added a LAMP stack, installed Nagios 4.1.1 and Nagios plugins 2.1.1.  I configured the install with the command [COLOR=#111111][FONT=monospace]--with-mail=/usr/sbin/sendmail[/FONT][/COLOR][COLOR=#000000][FONT=proxima-nova] in addition to all of the normal settings.  I now can still send test emails via the echo "blah" | mail -s "test" mymail.gmail.com, but everytime I try to send a notification from Nagios i am getting the error "ubuntu postfix/sendmail[#####]: fatal: usage: sendmail [options]" there is no other line in the logs associated with this entry, but this entry is generated everytime I try to send from Nagios.  My research has pointed to the fact that this may be a PHP scripting error, but I have not manually created any scripts.

Any help would be greatly appreciated.[/FONT][/COLOR]

---

### Post by mike405 on 2016-02-18
Ok so I was incorrect, this issue resided in the command.cfg for nagios.  /usr/sbin/sendmail -s $ABUNCHOFRANDOMSTUFF$
I added sudo in front of the -s and everything started working.

example below changes in bold and underlined

i hope this helps someone else out there
```

# 'notify-host-by-email' command definition
define command{
	command_name	notify-host-by-email
	command_line	/usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: $NOTIFICATIONTYPE$\nHost: $HOSTNAME$\nState: $HOSTSTATE$\nAddress: $HOSTADDRESS$\nInfo: $HOSTOUTPUT$\n\nDate/Time: $LONGDATETIME$\n" | _**/usr/sbin/sendmail sudo -s**_ "** $NOTIFICATIONTYPE$ Host Alert: $HOSTNAME$ is $HOSTSTATE$ **" $CONTACTEMAIL$
	}

# 'notify-service-by-email' command definition
define command{
	command_name	notify-service-by-email
	command_line	/usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: $NOTIFICATIONTYPE$\n\nService: $SERVICEDESC$\nHost: $HOSTALIAS$\nAddress: $HOSTADDRESS$\nState: $SERVICESTATE$\n\nDate/Time: $LONGDATETIME$\n\nAdditional Info:\n\n$SERVICEOUTPUT$" | _**/usr/sbin/sendmail sudo -s **_"** $NOTIFICATIONTYPE$ Service Alert: $HOSTALIAS$/$SERVICEDESC$ is $SERVICESTATE$ **" $CONTACTEMAIL$
	}
```

---

### Post by Ted_Dargis on 2016-04-04
I had almost the exact same problem. Clean install of 14.04 with Postfix etc. Then a clean install of Nagios but it wouldn't send even though command line mail testing worked. You saved me a substantial amount of time with your post!

Grazzi!

---

### Post by HermanAB on 2016-04-04
Sure, but you don't need Postfix for this;  ssmtp or nullmailer would do.

---

