---
title: "How to run a service using systemD with that user’s environment variables?"
date: 2022-01-06
forum: General Help
---

### Post by YourSurrogateGod on 2022-01-06
I’m using SytemD to run a bunch of services. One of them has the user as runtimeUser.

When I execute env in a script that’s called by rebuild_db.service, the number of env values that are set are about 6… typically for that user there are 30+. How can I start a service as a specific user with that user’s environment variables?

---

### Post by TheFu on 2022-01-07
You'll need to set the environment variables manually in the script that runs the program.  Just running under the userid won't fix this, since the interactive shell environment doesn't get used for systemd unit files OR crontab entries.

---

