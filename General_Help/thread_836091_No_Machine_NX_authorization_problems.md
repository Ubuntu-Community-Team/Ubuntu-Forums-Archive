---
title: "No Machine NX authorization problems"
date: 2008-06-21
forum: General Help
---

### Post by volkerbradley on 2008-06-21
Have spent several days now trying to get NoMchine Free NX working.
I seem to have an authorization problem.
When I give the command  nxserver --usercheck volker, I see:
NX> 900 Verifying public key authentication for NX user: volker.
NX> 900 Adding public key for user: volker to the authorized keys file.
NX> 716 Public key is already present in: /home/volker/.ssh/authorized_keys2.
NX> 900 Verifying public key authentication for NX user: volker.
NX> 500 ERROR: Public key authentication failed
NX> 500 WARNING: NX server was unable to login as user: volker
NX> 500 WARNING: Please check that the account is enabled to login.
NX> 500 WARNING: Also check that user's home directory, the directory
NX> 500 WARNING: ~/.ssh and the file ~/.ssh/authorized_keys2 have
NX> 500 WARNING: correct permissions according to the StrictModes of
NX> 500 WARNING: your SSHD configuration

It says: Please check that the account is enabled to login.  I have verified that I can ssh to my account from another computer.
Then it says to make sure that a number of files and directories have the correct permissions according to StrictModes of the SSHD configuration.
For the life of me, I cannot find what the correct permissions for StrictModes are.  I believe I may have changed some permissions of these files in the past and would love to correct them.
Thanks

---

