---
title: "gnome-keyring gpg2 and enigmail clash -- looking for work around"
date: 2016-02-29
forum: General Help
---

### Post by user41 on 2016-02-29
Enigmail version 1.9 requires gpg2, it refuses to use gpg 1.4. ([https://www.enigmail.net/index.php/en/faq?view=category&id=13#faqLink_3](https://www.enigmail.net/index.php/en/faq?view=category&id=13#faqLink_3))

gpg2 requires use of gpg-agent (see man gpg2, for example """--no-use-agent
              This is dummy option. gpg2 always requires the agent.""" )

gnome-keyring intercepts calls to gpg-agent and breaks the necessary (for email) gpgsm. The workaround documented is to disable Gnome keyring ([https://wiki.gnupg.org/GnomeKeyring](https://wiki.gnupg.org/GnomeKeyring)). 

I have Ubuntu 15.04. I use Gnome keyring to manage my encrypted backups, for example. So I can't disable it without losing that functionality. However this means Thunderbird/enigmail fails. The error is:
 """GnuPG reported an error in the communication with gpg-agent (a component of GnuPG).This is a system setup or configuration error that prevents Enigmail from working properly and cannot be fixed automatically.
We strongly recommend that you consult our support web site at https://enigmail.net/faq."""

Note that the FAQ the enigmail error points to is the one I quoted above, it does not provide a workaround for this conflict, although it provides advice on upgrading to gpg2. 

Is there a way for gpg-agent to manage the enigmail password? If not, am I stuck choosing between encrypted email and encrypted backup files? Can I roll back the version of enigmail? There is no obvious option to do this. I attempted to override the GnuPG location in engimails basic settings page back to gpg v1.4, but it caught that I'd rolled back major versions and refused to work. 

I attempted to provide an additional command to gpg via enigmails "advanced" options tab of `--agent-program /usr/bin/gpg-connect-agent'  and `--agent-program /usr/bin/gpg-agent' but that didn't help, gnome-keyring is intercepting the calls at a lower level than that. 

Can I edit gnome-keyring locally somehow to prevent it from intercepting these calls, and just let gpg-agent and gnome-keyring run in parallel? I assume that has other issues, but as currently nothing helps perhaps it is worth the tradeoffs?  

Any other workarounds available? Or am I just destined to use old software versions forever? 

Thanks for your help.

---

### Post by user41 on 2016-03-01
So I believe I've managed to sort this. You'll have to start thunderbird from the command line, though. Put the following in your ~/.bashrc file:

```
# this is necessary since enigmail in thunderbird requires gpg2, it no longer# works with the default gnome keyring.
# this is taken from the gpg-agent man page:
# /usr/bin/gpg-agent --daemon --write-env-file "${HOME}/.gpg-agent-info"
# which helps, but it spawns a new agent for each terminal. 
# adjusting for the advice here (even though it's for OSX):
## https://www.semipol.de/2015/05/03/letting-enigmail-use-gpg-agent-for-passphrase-caching-on-osx.html
# that is, make sure it's not running already (test the right file exists and
# that the pid it lists is running (kill -0 just checks if a pid is alive)
if test -f "$HOME/.gpg-agent-info" && \
     kill -0 "$(cut -d: -f 2 "$HOME/.gpg-agent-info")" 2>/dev/null
then
    echo "already running" > /dev/null
else
    /usr/bin/gpg-agent --daemon --write-env-file "${HOME}/.gpg-agent-info" > /dev/null
fi

# then do the rest of the stuff from the gpg-agent man page
# This should be run "for each interactive session"
if [ -f "${HOME}/.gpg-agent-info" ]
then
    . "${HOME}/.gpg-agent-info"
    export GPG_AGENT_INFO
fi

GPG_TTY=$(tty)
export GPG_TTY
```
This will be run whenever you open a new terminal, but will make sure you only have one gpg-agent running at a time.
Then, from a (new) terminal, initialize thunderbird (``thunderbird'' at the prompt should do it). I think that it then inherits the context from the terminal, including the gpg-agent. Either way, it works properly with encrypting and decrypting mail, without disabling gnome-keyring. 
I also have ``--agent-program /usr/bin/gpg-connect-agent'' in my enigmail preferences, advanced tab, for running gpg2 with that flag, but I don't think that should be needed.

---

