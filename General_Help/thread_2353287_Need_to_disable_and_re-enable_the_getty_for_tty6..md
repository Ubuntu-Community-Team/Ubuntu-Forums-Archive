---
title: "Need to disable and re-enable the getty for tty6."
date: 2017-02-20
forum: General Help
---

### Post by tcagle53 on 2017-02-20
I need to disable the respawn getty configuration of the tty6 console device to perform some other work and then be able to put it back to normal (respawn) behavior once that is done. This is necessary to support a certain software to operate via crontab entry in 16.04 LTS.

This software originally ran under SCO which had a dedicated enable/disable command for its' tty devices. This software was later ported to fedora and used editting of the inittab via sed to disable the respawn configuration to "off" and then executed "telinit q" to reload the disabled configurations. When the cron activity finished it would put inittab configuration back to its' original settings and "telinit q" again. Of course all this cron activity ran under the root login to achieve these effects which was fine for our purposes. 16.04LTS does not have the inittab so those old techniques won't work here.

Anyone have any tips or advice that might help?

---

### Post by #&amp;thj^% on 2017-02-20
This may or may not be what you wanted....but maybe an idea can come from it.
As Lennart says in a blog :

   >  In order to make things more efficient login prompts are now started on demand only. As you switch to the VTs the getty service is instantiated to [EMAIL="getty@tty2.servic"]getty@tty2.servic[/EMAIL]e, [EMAIL="getty@tty5.servic"]getty@tty5.servic[/EMAIL]e and so on. Since we don't have to unconditionally start the getty processes anymore this allows us to save a bit of resources, and makes start-up a bit faster.
A good read here: [http://0pointer.de/blog/projects/serial-console.html](http://0pointer.de/blog/projects/serial-console.html)
If you do wish to configure a specific number of gettys, you can, just modify logind.conf with the appropriate entry, in this example 3:

```
NAutoVTs=3
```
This method may not be ideal (for this case)...but worth offering none the less.
To disable gettys on particular TTYs 4-6 while possibly leaving 1-3 and 7-9 working, run:

for i in {4..6}; do
 ```
 systemctl mask getty@tty${i}.service
```
done.

mask creates symlink /etc/systemd/system/{name} -> /dev/null which effectively disables service. **Any attempt to run it via systemctl start will display error Failed to start NAME.service: Unit NAME.service is masked.**

If you have A.service Wants=masked.service, then start A will succeed but also will _generate dependency start error in journal_.

If you have B.service Requires=masked.service, then start B will also fail.

Credit to: jasonwryan (Arch forum Admin)
Hope this is useful to you.
Very good reading here: [http://0pointer.de/blog/projects/systemd-for-admins-1.html](http://0pointer.de/blog/projects/systemd-for-admins-1.html)
Note also look in "gedit /lib/systemd/system/getty.target.wants/getty-static.service"

---

### Post by tcagle53 on 2017-02-21
The suggested command:

systemctl mask [EMAIL="getty@tty6.servic"]getty@tty6.servic[/EMAIL]e


worked fine for my case by using it for permanent disablement of a single tty to use for my purposes. For completeness... I don't suppose you happen to know the appropriate command to reverse that change too? At any rate thanks for the quick response I am able to get past my issue with the above. I did have to install the systemd package as well since the systemctl was missing on this system as it stood (14.04). It is a VM based system I was doing this on, and it appears to launch all 6 agetty's by default somehow. I don't see that behavior on my non-vm ubuntu system here at home. They only seem to launch on demand at the hot key press for the desired console. Thanks again.

---

### Post by #&amp;thj^% on 2017-02-21
Sorry about that, I should have shown the reversal code in my first post...This works for me: (in my case use)
```
systemctl unmask getty@tty6.service
```
Mine shows:
```
me@me-750-417c:~$ systemctl mask getty@tty6.service
Created symlink from /etc/systemd/system/getty@tty6.service to /dev/null.
me@me-750-417c:~$ systemctl unmask getty@tty6.service
Removed symlink /etc/systemd/system/getty@tty6.service.
me@me-750-417c:~$ 

```
There is a lot of good reading on those links I included with my first post also.:)
Glad you found some use for it.
Kind Regards

---

