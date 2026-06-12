---
title: "OpenBox, open firefox and switch between links (URLs) with crontab."
date: 2021-12-09
forum: General Help
---

### Post by mateusguilhermedasilva on 2021-12-09
[COLOR=#232629][FONT=-apple-system]hi 

My openbox starts a link(URL) in kiosk mode by default (firefox -kiosk) specified in autostart.sh. I would like to schedule a crontab so that at 10:00 firefox would open another URL and at 11:00 it would return to the default url. Is it possible to do this with OpenBox?[/FONT][/COLOR]

---

### Post by ActionParsnip on 2021-12-09
Sure, you may need to specify the DISPLAY variable but yeah, no problem. I also recommend you suffix the command with an ampersand too.
You may also want to setup a monitor so that you don't have too many firefox processes running and send an alert in some way when there are lots

---

### Post by mateusguilhermedasilva on 2021-12-09
you suggest something like:


$export DISPLAY=mymachine.mydomain.com:0.0
$firefox "FirstUrl.com" & 

$firefox "SecondUrl.com" & 

sorry i'm a newbie with openbox

---

### Post by ActionParsnip on 2021-12-09
Sounds fine to me

---

