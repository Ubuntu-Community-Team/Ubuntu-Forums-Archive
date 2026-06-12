---
title: "Cacti not working-Ubuntu server 14.04-64bits."
date: 2015-02-26
forum: General Help
---

### Post by muhammad7 on 2015-02-26
hello all,

i am new to nix so have not got a clue where i am stuck at.

Trying to install cacti on ubuntu, i installed lamp, installed cacti. but after installing cacti i am unable to open the cacti install script over webpage. 
[http://serverip/cacti/install.php](http://serverip/cacti/install.php)
but

serverip/index.html is opening
serverip/phpmyadmin/index.php is also working

the error that i am getting is [h=1]No data received.[/h]any troubleshooting tips are appreciated.

---

### Post by tgalati4 on 2015-02-26
Cacti is a graphics framework for displaying data.  Normally it is used with *nagios*, the monitoring framework so cacti has data to display.  What do you want to use cacti for?

If you read through the install.php script and you see any references to nagios, then you might need to install it.

---

### Post by muhammad7 on 2015-03-02
i thought cacti and nagios are used to monitor devices and both can be used independently? i need to monitor mysql servers health using cacti.

---

### Post by tgalati4 on 2015-03-02
I found a few links:

[http://crunchtools.com/software/crunchtools/cacti/graph-mysql-stats/](http://crunchtools.com/software/crunchtools/cacti/graph-mysql-stats/)

[http://www.percona.com/doc/percona-monitoring-plugins/1.0/cacti/mysql-templates.html](http://www.percona.com/doc/percona-monitoring-plugins/1.0/cacti/mysql-templates.html)

[http://www.percona.com/software/percona-monitoring-plugins](http://www.percona.com/software/percona-monitoring-plugins)

[http://cdn.oreillystatic.com/en/assets/1/event/2/Benchmarking%20and%20Monitoring_%20Tools%20of%20the%20Trade%20_Part%20II_%20Presentation.pdf](http://cdn.oreillystatic.com/en/assets/1/event/2/Benchmarking%20and%20Monitoring_%20Tools%20of%20the%20Trade%20_Part%20II_%20Presentation.pdf)

[https://www.pitt-pladdy.com/blog/_20120426-165939_0100_MySQL_Performance_Graphs_on_Cacti_via_SNMP/](https://www.pitt-pladdy.com/blog/_20120426-165939_0100_MySQL_Performance_Graphs_on_Cacti_via_SNMP/)

---

