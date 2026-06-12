---
title: "azureus automagically loading with cron job"
date: 2006-10-25
forum: General Help
---

### Post by ser1alsn1per on 2006-10-25
hi i need to make a cron job to do the following 

open azureus at 12:00 midnight     

then close at 12:00 afternoon

does anyone know how to do this >?

---

### Post by matthewstory on 2006-10-25
well, it would be two cron jobs, the first script would look like this:

azureus

The second sript would look like this:

killall azureus

And you'd have to hand edit the crontab to get them to run at the times specified, which is a rather daunting task.

The other option would be to write a bash script like this:

#!/bin/bash
while [ 1 ]
do
azureus
sleep 43200
killall azureus
sleep 43200
done

Then start your script at midnight, it will open azureus, then sleep for 12 hours, then close azureus then sleep for 12 hours . . . and on and on and on and on . . .

---

### Post by mjziegle on 2006-10-25
rather than using azureus, i'd use btdownloadcurses for your scripting needs.

---

### Post by skymt on 2006-10-25
> **matthewstory said:**
> #!/bin/bash
while [ 1 ]
do
azureus
sleep 43200
killall azureus
sleep 43200
done

That would be:```
#!/bin/bash
while true
do
azureus &
sleep 43200
killall azureus
sleep 43200
done
```

EDIT: Also, I think rtorrent has build-in scheduling support. You'd have to keep it running all the time, but it can be in the background using screen.

---

### Post by matthewstory on 2006-10-27
while [ 1 ] is the same as while true, but yes, azureus & is fine, though if you run the script in the background ./script.sh & that shouldn't matter either way.

---

