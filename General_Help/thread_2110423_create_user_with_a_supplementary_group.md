---
title: "create user with a supplementary group"
date: 2013-01-30
forum: General Help
---

### Post by Drenriza on 2013-01-30
So i'am trying to create a new user with a supplementary group, but it will just not work.

```

useradd –m –G [group] –p [password] [username]

```

The "error" is get is that the terminal types back
> 
Usage: useradd [options] LOGIN

Options:
  -b, --base-dir BASE_DIR       base directory for the home directory of the
                                new account
  -c, --comment COMMENT         GECOS field of the new account
  -d, --home-dir HOME_DIR       home directory of the new account
  -D, --defaults                print or change default useradd configuration
  -e, --expiredate EXPIRE_DATE  expiration date of the new account
  -f, --inactive INACTIVE       password inactivity period of the new account
  -g, --gid GROUP               name or ID of the primary group of the new
                                account
  -G, --groups GROUPS           list of supplementary groups of the new
                                account
  -h, --help                    display this help message and exit
  -k, --skel SKEL_DIR           use this alternative skeleton directory
  -K, --key KEY=VALUE           override /etc/login.defs defaults
  -l, --no-log-init             do not add the user to the lastlog and
                                faillog databases
  -m, --create-home             create the user's home directory
  -M, --no-create-home          do not create the user's home directory
  -N, --no-user-group           do not create a group with the same name as
                                the user
  -o, --non-unique              allow to create users with duplicate
                                (non-unique) UID
  -p, --password PASSWORD       encrypted password of the new account
  -r, --system                  create a system account
  -s, --shell SHELL             login shell of the new account
  -u, --uid UID                 user ID of the new account
  -U, --user-group              create a group with the same name as the user
  -Z, --selinux-user SEUSER     use a specific SEUSER for the SELinux user mapping


As if it won't accept the options in the order or something.
Anyone who can tell me WHY! Is types back the usage of useradd when i try to add a simple user.

Thanks on advance.
Kind regards.

---

### Post by Warren Hill on 2013-01-30
Could be wrong but I think creating a user needs sudo

Try
     ```
sudo useradd &#8211;m &#8211;G [group] &#8211;p [password] [username]
```Or take a look here
[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

---

### Post by Drenriza on 2013-01-30
> **Warren Hill said:**
> Could be wrong but I think creating a user needs sudo

Try
     ```
sudo useradd –m –G [group] –p [password] [username]
```Or take a look here
[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

Valid point. But i'am already logged in as root (activated the root user)

---

### Post by Warren Hill on 2013-01-30
The link I gave recommends

```
adduser
```

instead of 

```
useradd
```
Not sure why

---

### Post by bantuvez on 2013-01-30
Does the GROUP name already exist?

---

### Post by Drenriza on 2013-01-31
> **bantuvez said:**
> Does the GROUP name already exist?

Yes :)

A more complicated way i got around this issue (as a pain in the butt as it is)
i created a user with
```
useradd -m [username]
usermod -p [password] [username]
usermod -G [group name] [username]
```

and it works fine.
I just cant figure out, why the one liner useradd does not work.
```
useradd –m –G [group] –p [password] [username]
```

---

