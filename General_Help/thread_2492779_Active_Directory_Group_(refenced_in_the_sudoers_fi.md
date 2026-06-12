---
title: "Active Directory Group (refenced in the sudoers file) is Intermittent via SSH"
date: 2023-11-22
forum: General Help
---

### Post by lovetolearn on 2023-11-22
Hello community!

**ENVIRONMENT**
We are operating several Ubuntu 22.04 systems. The systems are added to a Windows Active Directory Domain via the GUI as part of the initial configuration. We have an Active Directory group called "sudoers" that contains several Active Directory Users. We have modified the sudoers (/etc/sudoers) file via visudo to include the "sudoers" group from Active Directory. SSH is operating on the systems. 

Users are able to established a ssh session via their Active Directory credentials. Members of the "sudoers" Active Directory group are able to elevate commands from a ssh session. Sometimes.

**PROBLEM**
Intermittently, members of the suoders group will establish a ssh session, attempt to run an elevated command, and receive the "<username> is not in the sudoers file.  This incident will be reported." message. The problem seems to happen when more than one ssh session is established by the same user. The sudoers group is not displayed if the user runs the "groups" command while in the problem state. Yet, the sudoers group is displayed if the same user runs the "groups" command from a different ssh session (while the other ssh session is still in the problem state).

We've tried a number of configuration changes without success. Any guidance would be greatly appreciated!

[B]REFERENCES
[/B]I've listed the sudoers file contents and the sssd.conf (/etc/sssd/sssd.conf) file contents for reference.
```
## This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset
Defaults        mail_badpass
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"
Defaults        use_pty

# This preserves proxy settings from user environments of root
# equivalent users (group sudo)
#Defaults:%sudo env_keep += "http_proxy https_proxy ftp_proxy all_proxy no_proxy"

# This allows running arbitrary commands, but so does ALL, and it means
# different sudoers have their choice of editor respected.
#Defaults:%sudo env_keep += "EDITOR"

# Completely harmless preservation of a user preference.
#Defaults:%sudo env_keep += "GREP_COLOR"

# While you shouldn't normally run git as root, you need to with etckeeper
#Defaults:%sudo env_keep += "GIT_AUTHOR_* GIT_COMMITTER_*"

# Per-user preferences; root won't have sensible values for them.
#Defaults:%sudo env_keep += "EMAIL DEBEMAIL DEBFULLNAME"

# "sudo scp" or "sudo rsync" should be able to use your SSH agent.
#Defaults:%sudo env_keep += "SSH_AGENT_PID SSH_AUTH_SOCK"

# Ditto for GPG agent
#Defaults:%sudo env_keep += "GPG_AGENT_INFO"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# Added Manually
%sudoers        ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "@include" directives:

@includedir /etc/sudoers.d
```

```
[sssd]
domains = domain.local
config_file_version = 2
Services = nss, pam

[domain/domain.local]
default_shell = /bin/bash
krb5_store_password_if_offline = True
cache_credentials = True
krb5_realm = DOMAIN.LOCAL
realmd_tags = manages-system joined-with-adcli
id_provider = ad
fallback_homedir = /home/%u@%d
ad_domain = domain.local
use_fully_qualified_names = False
ldap_id_mapping = True
access_provider = ad

#ldap_schema = rfc2307bis
#ldap_group_name = cn
#ldap_group_member = member
```

---

### Post by MAFoElffen on 2023-11-22
<<This is a Server Admin Question and would be dealt with better in the Server Section>>

Why?  You are a Windows Admin right? LOL I do both, so will translate this for you.

Apply the same basic foundation concepts...

You created a group named "sudoers" as a security group, and modified the "sudoers" file which does not affect the new "sudoers" group members, but rather members of the "sudo" group. The name you gave it is somewhat ambiguous, as it is confusingly named the same as that control configuration file... The confusion of that only starts with the name of that file, and goes from there onto other things and sections of the system:
sudoers policies in LDAP
sudo.conf, with it's contents and arguments: Plugin sudoers_policy sudoers.so sudoers_mode=0400 sudoers_uid=<XXXX> sudoers_gid=<gid_sudoers_file=<path> sudoers_mode=<mode>

Your can see where using that "name" as a "name" is a potential conflict waiting to happen right?

We usually, by rule of thumb use something descriptive like "sudousers"... Users are members of groups. You can add groups with sudo rights in the sudoers file by adding a line to /etc/sudoers similar to this:
```

%sudousers ALL=(ALL) ALL

```
Just like in Windows, where you can check the inherited rights of a specific user, you check the rights of a user added to a sudo enabled security group like this:
```

mafoelffen@Mikes-B460M:/data/ISO$ sudo -l -U mafoelffen
[sudo] password for mafoelffen: 
Matching Defaults entries for mafoelffen on Mikes-B460M:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin, use_pty

User mafoelffen may run the following commands on Mikes-B460M:
    (ALL : ALL) ALL

```
But if you the want to get down to details in what they can do, then 
```

# Allow user 'fred' to remote poweroff
fred ALL=(ALL) !ALL # deny all commands
fred ALL=NOPASSWD: /sbin/poweroff #specific commands they can do, without having to enter a password...

```

---

### Post by lovetolearn on 2023-11-27
Thank you for the message.

Per your suggestion, we may plan to rename the group to alleviate confusion.

We did add the "sudoers" Active Directory group to the sudoers file (/etc/sudoers).

```
# Added Manually
%sudoers ALL=(ALL:ALL) ALL
```

And members of the "sudoers" Active Directory group are able to elevate commands from a ssh session. Sometimes.

Intermittently, members of the "suoders" group will establish a ssh session, attempt to run an elevated command, and receive the "<username> is not in the sudoers file. This incident will be reported."

When the ssh session is in the problem state, the user can establish the second ssh session, attempt to run an elevated command, and it will work. Sometimes. The problem is intermittent.

It seems to be an Active Directory group membership problem that manifests itself when a ssh session is established. Sometimes. Additionally, the problem seems to only happen when more than one ssh session is established by the same user. We have been unable to recreate the problem state when a user establishes a single ssh session.

---

### Post by MAFoElffen on 2023-11-28
Wow. I haven't seen that being a problem in Linux, SSH and groups, with Windows AD DS out of the picture. 

Hmmm. I'm going to have to spin up my SSSD test-cases (Win Server DC controller and Ubuntu Domain members) and see if I can recreate that. You have me curious now.

---

