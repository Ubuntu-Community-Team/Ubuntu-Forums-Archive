---
title: "Ubuntu - Docker - Cron"
date: 2024-09-30
forum: General Help
---

### Post by doubledutch1962 on 2024-09-30
I run a version of Ubuntu (22.04 / Jamie-221130) in a Container on a QNAP NAS. But this Ubuntu image does not seem to include crontab. I've installed both the systemd and cron packages but I can't start them as it returns the error:

systemctl start systemd
System has not been booted with systemd as init system (PID 1). Can't operate.

And I have no idea how to physically reboot the system as the container manager does not seem to do a reboot even when I reboot the NAS, it just pauses the contain state and starts it up again.

What I want to do is run a script every time I reboot the NAS but I can't think of how to do this without getting systemd or cron to run. Any suggestion would be greatly appreciated.

---

### Post by adhesivereading on 2024-09-30
Running a cron job or using systemd in a container can be tricky, especially if your container isn't set up to run with systemd as the init system. You might consider running a script on startup in your Ubuntu container on your QNAP NAS. Using a startup script in a Container: You can modify the container's entrypoint to execute your script whenever the container starts. You can do this by adding your script to the entrypoint in your Dockerfile or container configuration:
chmod +x /path/to/your/script.sh


Modifying the container's entrypoint: If you're using Docker, you can do this in your Dockerfile:
ENTRYPOINT ["/path/to/your/script.sh"][RIGHT][SIZE=1][[COLOR=#ebece4]planet clicker[/COLOR]]("https://planet-clicker.com")[/SIZE]


[/RIGHT]

---

### Post by doubledutch1962 on 2024-10-01
Thank you - I did not consider that option. Having looked at it now, I can not find a way of configuring a startup script on my QNAP NAS (it does not seem to have that option).

I then found [this thread]("https://askubuntu.com/questions/1469337/ubuntu-22-04-jammy-run-script-on-resume") but that doesn't seem to work either. The script mentioned does no seem to execute, I guess because systemd is not running/

---

