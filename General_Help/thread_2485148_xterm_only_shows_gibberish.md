---
title: "xterm only shows gibberish"
date: 2023-03-21
forum: General Help
---

### Post by mr-overocker on 2023-03-21
I'm a high school teacher using ubuntu and xterm to manage 30+ student Raspberry Pi's. This combination has been working for years, but suddenly xterm is only showing gibberish [IMG]https://drive.google.com/file/d/1w13aSRRFp_6kodN5eqFTnqwaSjzhkIUv/view?usp=sharing[/IMG]  

Here is a link to a screen shot. 

[https://drive.google.com/file/d/1w13aSRRFp_6kodN5eqFTnqwaSjzhkIUv/view?usp=sharing](https://drive.google.com/file/d/1w13aSRRFp_6kodN5eqFTnqwaSjzhkIUv/view?usp=sharing)

I've tried reinstalling xterm with no change. 

Any help would be graciously appreciated. 

Thanks!

---

### Post by ActionParsnip on 2023-03-21
If you SSH to the Pi is it OK?

---

### Post by TheFu on 2023-03-21
If I was managing 30 computers, I'd be using ansible or clusterSSH.  Ansible being the better option.

BTW, the link never showed any image to me.

---

### Post by MAFoElffen on 2023-03-21
???

I saw the link. It seems to be a rendering problem of some type. Since I can see it, but other cannot. I'll dl it and upload it as an attachment so others can see it.

On just opening xterm you get that? What happens if you press <Cntrl><Alt><F4> and toggle to VTTY4?

@et-all -- His screenshot is attached to my post...

---

### Post by mr-overocker on 2023-03-22
I can ssh into the pi without any issue using the normal terminal. 

I use cssh to manage all the pi's at once and that uses xterm. 

If I open xterm directly I get the same giberish.

---

### Post by mr-overocker on 2023-03-22
<Cntrl><Alt><F4>  
Just pops me to a text login screen . ... I can log in just fine, but can't launch xterm from that.

---

### Post by TheFu on 2023-03-22
> **mr-overocker said:**
> I can ssh into the pi without any issue using the normal terminal. 

I use cssh to manage all the pi's at once and that uses xterm. 

If I open xterm directly I get the same giberish.

So, the way to have a remote xterm with GUI on other systems is to use:
```
xterm -geometry 80x25-5+78 $XTERM_OPTS -e ssh -X istar &
```

For managing 30 systems, I'd still use ansible.  Running a command on all 30 isn't hard. You'll need to setup an 'inventory' file which can list each DNS name or use a range of IPs on a single line, if you like.
Then to run the same command on each, use something like this:
```
$ ansible -i hosts -a "cat /var/run/reboot-required" current
```
where
[LIST]
[*]hosts is my inventory file
[*]current is the grouping of my hosts to have the command run against.
[/LIST]
Part of my inventory file looks like this:
```
[cur]
ubudesk
redmine
zcs43
qbe
deneb         ansible_connection=local
pi3           ansible_user=osmc

[students]
u-[50-99]pi.example.com


```
There are options that can be added to the inventory file, like which user ssh needs to connect with. Otherwise, the ~/.ssh/config file will be used or the same userid as running ansible will be used.
Of course, ansible is meant to manage systems, so it has methods to modify config files, restart daemons, push new files over (copy or templated) and do package management. Anything that can be scripted can be controlled via ansible, which generally means anything.
I'm running the default ansible from the Ubuntu packages.
```
$ ansible --version
ansible 2.10.8

```

Anyway, wanted to show an easy, 1-command, example.

---

### Post by Holger_Gehrke on 2023-03-22
If xterm is broken and a reinstall doesn't change that, then it's most probably a user specific configuration. Create a new user, login to that account and check whether xterm behaves right on that account. If it does, then we will have to hunt up the (mis-) configuration on your normal account, which isn't quite as simple as with other terminal programs since xterm uses the old xrdb mechanism, a kind of in-memory database of configuration strings which can be fed from arbitrary files, so any (text-) file might get merged into the database and play mischief with the configuration. You can get a listing of the resources configured for xterm with 'appres XTerm' or 'appres XTerm-color'. The default files which get loaded into the resource database are '~/Xresources' and / or '~/.Xdefaults', but there's way more than that, for example there are xterm-specific files of resources in '/etc/X11/app-defaults/XTerm' and '/etc/X11/app-defaults/Xterm-color'.

Also, xterm has three pop-up-menus you can open by holding ctrl and one of the mouse buttons (each mouse button opens a different menu, the menu closes when you release the button). There might be some unusual option set this way, worth a check at least.

'cssh' ? Is that [clusterssh]("https://github.com/duncs/clusterssh") ? The documentation on github states that you can set the terminal to use with a 'terminal = path-and-filename-for-terminal' line in ~/.clusterssh/config. Might be worth a try to set that to another terminal program ...

Holger

---

