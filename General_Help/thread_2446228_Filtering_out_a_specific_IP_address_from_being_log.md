---
title: "Filtering out a specific IP address from being logged into Apache2 access.log file"
date: 2020-06-26
forum: General Help
---

### Post by jwilsonjr on 2020-06-26
Using Ubuntu 20.04 LTS

I have been attempting to find information on how to *filter out a specific IP Address* from being logged by Apache2's access.log.

I have found many articles on how to configure the log file but nothing about omitting a common IP address that is over-filling the log file. Can anyone point me in the right direction? It would be greatly appreciated.

Thank You in advance...

Jack

---

### Post by Skaperen on 2020-06-26
you configure the log "file" to be a shell command.  enter the file name in double quotes and put a vertical bar at the front of the command.  then make the command on that filters out that IP address and writes the data to the real file name intended.  i used to split logs into individual files years ago with a C program i wrote that i ran under apache.  i hope it still works the same way.  i can't imagine them taking the feature out but they could have changed the way it works.

---

### Post by dragonfly41 on 2020-06-26
I happen to be looking at vhosts in apache2 and how to quickly reconfigure configurations .. I am studying [mod_macro]("http://www.cfg.uk/manual/en/mod/mod_macro.html") which might be worth looking at.
Different logging macros can be defined.

---

### Post by SeijiSensei on 2020-06-26
Is this traffic from a valid address or junk you want to stop logging?

If the latter, I'd just block the IP address entirely inside Apache2.

In the <Directory> stanza for the web site, use something like this:
```

<Directory "/path/to/the/site/root">
<RequireAll>
    Require all granted
    Require not ip 10.10.10.10
</RequireAll>
[stuff]
</Directory>

```
replacing 10.10.10.10 with the address you wish to block.

See [https://httpd.apache.org/docs/2.4/howto/access.html](https://httpd.apache.org/docs/2.4/howto/access.html) for details.

You could also block it with an iptables rule, but this works within Apache2. Don't forget to restart the server with "sudo systemctl restart apache2".

---

### Post by jwilsonjr on 2020-06-26
Good Afternoon,

Thank you for your response. In response to your question, the IP address is actually an internal network IP Address that is valid but just has a lot of activity that I do not want to keep sifting through in the access.log. So not looking to block the IP from access, just filter it out from the log.

Jack

---

### Post by SeijiSensei on 2020-06-27
Take a look at the section on "Conditional Logs" in [https://httpd.apache.org/docs/2.4/logs.html](https://httpd.apache.org/docs/2.4/logs.html).  SetEnvIf sets an environment variable "dontlog" for addresses that match the conditionals.  Then the CustomLog line excludes them with "env=!dontlog".

---

### Post by jwilsonjr on 2020-06-27
Thank you! That worked nicely. Appreciate the help.

Jack

---

