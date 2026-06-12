---
title: "Syntax error: Unterminated quoted string"
date: 2013-01-31
forum: General Help
---

### Post by chrisolido on 2013-01-31
im getting Syntax error: Unterminated quoted string when i ran this script ..
  

#!/bin/bash
  REPO='myrepo'
ORG_NAME='repo'
KEY_NAME=`hostname`
  ssh-keygen -b 4096 -t rsa -f /${USER}/.ssh/${REPO}_rsa -P ""
  SSH_KEY = "/${USER}.ssh"/${REPO}_rsa.pub"
  # Trim extraneous trailing lines
SSH_KEY=$(cat ${SSH_KEY} | tr -d '\n')
  curl -d "{\"title\": \"${KEY_NAME}\", \"key\": \"${SSH_KEY}\"}" -H "Authorization: token ${GITHUB_API_KEY}" [https://api.github.com/repos/$](https://api.github.com/repos/$){ORG_NAME}/${REPO}/keys 
  can you help me to solve that issue...
I just want to automate my connectivity with github when i boot a machine.

---

### Post by dcstar on 2013-02-01
> **chrisolido said:**
> im getting Syntax error: Unterminated quoted string when i ran this script ..
  

#!/bin/bash
  REPO='myrepo'
ORG_NAME='repo'
KEY_NAME=`hostname`
  ssh-keygen -b 4096 -t rsa -f /${USER}/.ssh/${REPO}_rsa -P ""
 ** SSH_KEY = "/${USER}.ssh"/${REPO}_rsa.pub"**
...........

I suppose the UNEVEN quantity of quotes in that line might have something to do with it.

---

