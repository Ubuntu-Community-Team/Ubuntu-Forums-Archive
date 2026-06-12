---
title: "More of a sed -i question. Related Unattended Upgrade"
date: 2023-12-16
forum: General Help
---

### Post by ccwilson on 2023-12-16
Hi 
I am trying to get the unattended upgrades working. 
The process I have used is to install

```
sudo apt install unattended-upgrades -y

```

I have to edit the config file

/etc/apt/apt.conf.d/50unattended-upgrades

the top of the looks like this:

```
// Automatically upgrade packages from these (origin:archive) pairs
//
// Note that in Ubuntu security updates may pull in new dependencies
// from non-security sources (e.g. chromium). By allowing the release
// pocket these get automatically pulled in.
Unattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}";
        "${distro_id}:${distro_codename}-security";
        // Extended Security Maintenance; doesn't necessarily exist for
        // every release and this system may not have it installed, but if
        // available, the policy for updates is such that unattended-upgrades
        // should also install from here by default.
        "${distro_id}ESMApps:${distro_codename}-apps-security";
        "${distro_id}ESM:${distro_codename}-infra-security";
//     "${distro_id}:${distro_codename}-updates";
//      "${distro_id}:${distro_codename}-proposed";
//      "${distro_id}:${distro_codename}-backports";
};




```


I want to strip the // of the line ```
//     "${distro_id}:${distro_codename}-updates";
```

I have already achieved this for some of the other lines in the file, but this line refuses to budge. Any one know why?

for example:
this line works and removes teh leading slashes and changes teh time

```
sudo sed -i 's/\/\/Unattended-Upgrade::Automatic-Reboot-Time \"[0-9][0-9]:[0-9][0-9]"/Unattended-Upgrade::Automatic-Reboot-Time "04:30"/g' /etc/apt/apt.conf.d/50unattended-upgrades
```


So that works. But regarding the line above

```
sed -i 's/\/\/      "${distro_id}:${distro_codename}-updates";/        "${distro_id}:${distro_codename}-updates";/g' /etc/apt/apt.conf.d/50unattended-upgrades
```

does not work

Yet when I test it online at [https://sed.js.org/#](https://sed.js.org/#) it work there?

I am at a loss. this is probably the most relevant line to getting teh updates to actually install.

Any one got some idea why it won't work? or how I can strip this two slashes off the front?


TIA
Chad

---

### Post by Holger_Gehrke on 2023-12-16
I'm not totally certain why your sed-script doesn't work, but I think it might have something to do with the '{}' or the '$'. Braces are qualifiers in a lot of regular expression languages (e.g. 'a{4,5}' means "four or five times 'a'"). And '$' is the end of the line. So using a regular expression as an address for the 's///' command and keeping the expressions in s/// short might help.
When I tried
```

sed -e '/-updates";$/ s#//##' /etc/apt/apt.conf.d/50unattended-upgrades

```
it seemed to work. It looks for a line ending (that's the '$' in the address) in '-updates";' and replaces '//' with an empty string on that line.

Holger

---

