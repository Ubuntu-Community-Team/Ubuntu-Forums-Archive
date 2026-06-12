---
title: "Gaim won't lauch"
date: 2006-12-04
forum: General Help
---

### Post by stevekl on 2006-12-04
Running Edgy here, and gaim won't launch. When I click on the icon in my menu bar, I get the wait cursor and nothing happens. When I issue the 'gaim' command in a terminal, nothing happens (as in, it just goes back to the prompt). I've tried dpkg-reconfigure and it doesn't fix it. I am fully upgraded. Is this happening to anyone else? Anyone have a suggestion?

---

### Post by SuperMike on 2006-12-04
Right after you run the command and fail, what does a 'tac /var/log/messages | more' show near the top -- anything about Gaim?

Did you confirm you have a /usr/bin/gaim?

What happens if you run the gaim command under root like:

**sudo passwd root**
[type your password]
[type new root password]
[reconfirm new root password]
**su**
[type new root password]
[B]gaim
[/B]

Have you tried this?

[B]sudo apt-get --purge remove gaim
sudo apt-get install gaim
gaim
[/B]

---

