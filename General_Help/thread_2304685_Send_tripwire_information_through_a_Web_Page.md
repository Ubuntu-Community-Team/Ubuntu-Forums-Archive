---
title: "Send tripwire information through a Web Page"
date: 2015-11-29
forum: General Help
---

### Post by Harley_Frank on 2015-11-29
To clarify, I have 2 digital ocean VPS setup. One is my MySQL server and also a file server, and the other one is my main one. Since the main one is setup and ready to go, I added tripwire, thought I would do the same except I realized that second VPS doesn't get out to the internet because I have the main ethernet locked down. I only open it up for updates, but its connected via a tunnel over the private network.

What I want to do is create a cronjob on my main machine that runs tripwire on the other machine and saves the report in a text file in the main machine's /srv/tripwire_reports and then a minute later another cronjob runs the webpage /srv/tripwire_reports/email. Inside that webpage would have PHPmailer attach the text file and email it to me. I don't know enough about tripwire, and looking into this specific thing I haven't found any similar google searches.

To further clarify I am talking about Cron jobs here, I here it only works on the local machine you're using but I hope that isn't the case. Also the reason why I want to use a webpage is because my mailhost has some janky security things and using my server to relay won't authenticate, however, it would from a webpage. Don't understand.

I have tried to configure exim4 because I have ajenti v installed. I have done it through my mail account and then tried it with google. Don't understand why it would go through there, it always works. I have done many mail tests and it just doesn't wanna go through.

Any help would be much appreciated.

---

