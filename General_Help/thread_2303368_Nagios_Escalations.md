---
title: "Nagios Escalations"
date: 2015-11-18
forum: General Help
---

### Post by mcparty2 on 2015-11-18
I have been given a challenge to get Nagios to Escalate to the following requirements... I have been scratching my head for weeks now which I why I look to you. After reading all the Nagios documentation on escalations, I am guessing I am probably getting my logic wrong.

1, In working hours - only send one alert to admins (I can do this bit)
2, Out of hours & after 20minutes of the host being down, send only one alert to oohcontacts

Can any one see anything obviously wrong with the config as I am going nuts. The preflight test passes the config and picks up no syntax errors.

```

[COLOR=#454545][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#454545][FONT=Helvetica]define host {[/FONT][/COLOR]
[COLOR=#454545][FONT=Helvetica]     use                premier[/FONT][/COLOR]
[COLOR=#454545][FONT=Helvetica]     host_name    Test A4[/FONT][/COLOR]
[COLOR=#454545][FONT=Helvetica]     alias              Test[/FONT][/COLOR]
[COLOR=#454545][FONT=Helvetica]     address                    10.10.10.10[/FONT][/COLOR]
[COLOR=#454545][FONT=Helvetica]     hostgroups               premier[/FONT][/COLOR]
[COLOR=#454545][FONT=Helvetica]     notification_interval   20[/FONT][/COLOR]
[COLOR=#454545][FONT=Helvetica]     notification_options    d,r[/FONT][/COLOR]
[COLOR=#454545][FONT=Helvetica]     max_check_attempts      2[/FONT][/COLOR]
[COLOR=#454545][FONT=Helvetica]}[/FONT][/COLOR]
[COLOR=#454545][FONT=Helvetica]
define hostescalation{[/FONT][/COLOR]
[COLOR=#454545][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#454545][FONT=Helvetica]        hostgroup_name      premier[/FONT][/COLOR]
[COLOR=#454545][FONT=Helvetica]        contact_groups      oohcontacts[/FONT][/COLOR]
[COLOR=#454545][FONT=Helvetica]        first_notification  2[/FONT][/COLOR]
[COLOR=#454545][FONT=Helvetica]        last_notification  2[/FONT][/COLOR]
[COLOR=#454545][FONT=Helvetica]        escalation_period nonworkhours[/FONT][/COLOR]
[COLOR=#454545][FONT=Helvetica]        escalation_options  d,u[/FONT][/COLOR]
[COLOR=#454545][FONT=Helvetica]        }[/FONT][/COLOR]
[COLOR=#454545][FONT=Helvetica]
[/FONT][/COLOR]

```


Many thanks in advance.

McParty

---

### Post by mcparty2 on 2015-11-27
I managed to fix this. My main issue was that the timeperiods for my contacts were not right so all my tests were not working.
My config for escalations out of hours needed tweaking too. For the archives and anyone else trying escalations - Here is the config I used:

```
define hostescalation{

       hostgroup_name     premier
       contact_groups      admins
       first_notification 1
       last_notification  1
       notification_interval 20
       escalation_period nonworkhours
       escalation_options  d,u
       }

define hostescalation{

hostgroup_name      premier
       contact_groups      oohcontacts
       first_notification  2
       last_notification  2
       escalation_period  nonworkhours
       escalation_options  d,u
       }


```

---

