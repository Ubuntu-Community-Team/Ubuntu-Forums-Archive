---
title: "Cron and Tomboy Notes"
date: 2007-09-13
forum: General Help
---

### Post by munruh on 2007-09-13
I am wanting to use cron and tomboy notes to remind myself to breath deeper to help me feel better and be more alert. 

See: [http://www.kahunka.org/articles_with_video/breathing_tips.html](http://www.kahunka.org/articles_with_video/breathing_tips.html)

I have a crontab entry with the following:

>  # one minute for testing only (change to 10 or 15 minutes)
>  */1 * * * * DISPLAY=:0. exec /usr/bin/tomboy --open-note breath


For testing I created a shell script to test the command

>  DISPLAY=:0. exec /usr/bin/tomboy --open-note breath

and it works perfect when the script is called from xterm.

I also added an entry to crontab to append the time and date to a text file every minute so I could be sure cron is in working, and it is.


I assume it is just a syntax difference from the bash shell script and the crontab entry. What would be different between the way cron would execute a command and the bash shell?

I added a line to crontab  to run other GUI apps with command line arguments and they all worked. This seems to be a thing with tomboy notes.  :confused:

There maybe other ways to accomplish this, but I hate to be defeated

Any ideas?

Thank you!

---

