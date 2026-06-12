---
title: "connecting to a ssl selfsigned server."
date: 2022-10-06
forum: General Help
---

### Post by mudassarkhan on 2022-10-06
[LIST=1]
[*][COLOR=#232629][FONT=-apple-system]I have just dived in to linux/ubuntu over the last week or so. I've been following guides and tinkering on a clean server, so I had no worries of messing anything up.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I ran a nextcloud app on another server and then followed a guide to make a high peformance server to connect to the talk app.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]After nearly a week of following guides, reimaging the server, following guides ,reimaging the server I have finally got to, what i think is the last stage.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system][/FONT][/COLOR]
[*][COLOR=#232629][FONT=-apple-system]I set up the server installing coturn (which was an issue itself because simple 'install coturn' didn't work and I spent a day finding a way to get it installed).[/FONT][/COLOR]
[*][COLOR=#232629][FONT=-apple-system][/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]Then installing Janus[/FONT][/COLOR]
[*][COLOR=#232629][FONT=-apple-system][/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]Then Nats server[/FONT][/COLOR]
[*][COLOR=#232629][FONT=-apple-system][/FONT][/COLOR]Then nextcloud-spreed-signaling server
[*][COLOR=#232629][FONT=-apple-system]and finally nginx and set up a vhost.[/FONT][/COLOR]
[*][COLOR=#232629][FONT=-apple-system][/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]After multiple set backs I have finally got to a stage where my turn server set up is working.[/FONT][/COLOR]
[*][COLOR=#232629][FONT=-apple-system][/FONT][/COLOR]
[*][COLOR=#232629][FONT=-apple-system]However when I try and access the signaling server I get an error in nextcloud.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I have found the source of the issue When I run:[/FONT][/COLOR]
curl -i [https://signaling.domain.co.uk/standalone-signaling/api/v1/welcome](https://signaling.domain.co.uk/standalone-signaling/api/v1/welcome)
[COLOR=#232629][FONT=-apple-system]From the hosting server I get the response:[/FONT][/COLOR]
[*]
[*]{"nextcloud-spreed-signaling":"Welcome","version":"c8ff009635cb1133a690fe1bdcf5b248c"}
[*]
[COLOR=#232629][FONT=-apple-system]When I go direct to the url I also get the same message.[/FONT][/COLOR]
[*][COLOR=#232629][FONT=-apple-system][/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]However when I run the curl command from the server hosting nextcloud the error I get is:[/FONT][/COLOR]
curl: (60) SSL certificate problem: self-signed certificate
[*]
[*]
[COLOR=#232629][FONT=-apple-system]I didn't really have to be sherlock to figure out the issue but this seems to be the last hurdle I cannot overcome.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I cannot find a way for me to allow my server to connect to self signed service?[/FONT][/COLOR]
[/LIST]

---

### Post by dnisbet on 2022-10-06
Try curl with the -k switch.

---

