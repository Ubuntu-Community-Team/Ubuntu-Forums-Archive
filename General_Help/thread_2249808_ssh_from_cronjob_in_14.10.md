---
title: "ssh from cronjob in 14.10"
date: 2014-10-24
forum: General Help
---

### Post by shochatd on 2014-10-24
I just upgraded to 14.10 and ran into a complication. In previous releases, by simply attempting to use ssh from bash, I'm prompted for my passphrase and ssh-agent is run automatically (and has my private key). I could then put the resulting SSH_AGENT_PID and SSH_AUTH_SOCK settings into a small script to be sourced by my cron job so that it can use ssh. But in 14.10, I discovered that ssh-agent is no longer run in this case. I am, however, able to run ssh without my passphrase after this, so I think gnome-keyring must be doing all the work now. It seems like there should be a way to get my cron job to access gnome-keyring when it needs to use ssh. How is this done? There is an old forum post about this (from 2011) but the solution given there depends on the existence of ~/.dbus which does not exist on my 14.10 system. In the meantime, I have found that I can run ssh-agent and ssh-add myself and do things the "old" way (without gnome-keyring), but it seems like there should be some way to access gnome-keyring from my cron job without running ssh-agent, as seems to be working now in my interactive session.
Thanks.
-- David

---

### Post by shochatd on 2014-10-25
I have learned a bit more. When I log in, gnome-keyring-daemon is started automatically and SSH_AUTH_SOCK is set. gnome-keyring-daemon apparently acts as the SSH agent. Once logged in, I try ssh'ing to a remote host (that has my public key in authorized_keys). This gives a (graphical) prompt for my SSH passphrase. From now on, I can use ssh (and scp, etc.) without a passphrase, so the agent functionality is obviously working and my private key has apparently been "added" to this agent. I now believe that only SSH_AUTH_SOCK is needed in the cron script and that the only reason for keeping track of SSH_AGENT_PID was to support various schemes for killing the standard ssh-agent. Since we are not running the standard ssh-agent, we don't really need SSH_AGENT_PID. If my cron job works with the one environment variable, I'll mark this SOLVED.

---

