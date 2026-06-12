---
title: "gpg (Gnupg) command not popping up UI passphrase dialog box in awesome"
date: 2017-07-15
forum: General Help
---

### Post by amitst on 2017-07-15
When I login to default Ubuntu's window manager (Unity) and if I type the following command,

```
gpg --decrypt ~/file.gpg
```

I get a UI popup for entering the passphrase.

However, when I login through `awesome` window manager I don't get the UI popup and gpg-agent is not connected. What might be the reason?

I have following code in ~/.xsessionrc file while logging in to awesome.

```
# GnuPG agent (avoid repeatedly putting passphrase)
gnupglog="${HOME}/.gnupg/gpg-agent.info"
if (pgrep -u "${USER}" gpg-agent); then
  eval `cat ${gnupglog}`
  eval `cut -d= -f1 ${gnupglog} | xargs echo export`
else
  eval `gpg-agent --enable-ssh-support --daemon`
fi
```

Any suggestions to get the UI passphrase (or even command line passphrase that will be cached)?

Ubuntu 16.04 LTS

---

### Post by amitst on 2017-07-17
I found the root cause of the issue. gpg-agent should automatically set $GPG_AGENT_INFO during invocation but it is not setting the env variable. Similarly the file gpg-agent.info was not present as mentioned in the above post hence the above code wasn't working. As per the gpg documentation GPG_AGENT_INFO should point to the gpg-agent socket file followed by pid of gpg-agent and then the protocol (default 1). These three fields should be separated by colon.

So I put the following code in my ~/.profile to solve the issue (S.gpg-agent file is the socket file created by gpg-agent after it starts),
```

if (pgrep -u "${USER}" gpg-agent); then
  export GPG_AGENT_PID=`pgrep -u ${USER} gpg-agent`
  export GPG_AGENT_INFO=${HOME}/.gnupg/S.gpg-agent:${GPG_AGENT_PID}:1
else
  eval `gpg-agent --enable-ssh-support --daemon`
  export GPG_AGENT_PID=`pgrep -u ${USER} gpg-agent`
  export GPG_AGENT_INFO=${HOME}/.gnupg/S.gpg-agent:${GPG_AGENT_PID}:1
fi

```

Still I am not sure why gpg-agent is not able to set GPG_AGENT_INFO.

---

