---
title: "GPG-agent just doesn't work."
date: 2006-12-23
forum: General Help
---

### Post by mjgoins on 2006-12-23
I've installed the most recent versions of gpg and gpg-agent for dapper, and when I try to decrypt a file, I get:

> #gpg --decrypt file.gpg

<stuff removed for brevity...>

gpg: problem with the agent - disabling agent use
Enter passphrase:

I've googled this issue pretty heavily to no avail. I have confirmed that the GPG_AGENT_INFO variable is set correctly:

$ env | grep GPG
GPG_AGENT_INFO=/tmp/gpg-19Ukkj/S.gpg-agent:13108:1

and "use-agent" is obviously already in my gpg.conf file.

I have no idea what else could be going on here. Any suggestions are very welcome!

---

