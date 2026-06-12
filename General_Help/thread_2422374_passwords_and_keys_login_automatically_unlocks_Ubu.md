---
title: "passwords and keys login automatically unlocks Ubuntu 18.04 LTS"
date: 2019-07-06
forum: General Help
---

### Post by mIk3_08 on 2019-07-06
passwords and keys login automatically unlocks Ubuntu 18.04 LTS

Is there any way that this passwords and keys login won't automatically unlock every time I power on my system. I always perform this locking every time I turn on my system. This all start when I try to use my online accounts and now I'm still using it. 
Any response will be much appreciated.

---

### Post by crip720 on 2019-07-06
Not quite sure what you are asking, if you don't want to put in password everytime you boot your computer you can just turn on automatic login in system settings(ubuntu unity).  This would cause the 'passwords and keys' app to stay lock until you put your password

---

### Post by again? on 2019-07-06
The login keyring uses the same password as your login password.
To not unlock the keyring when you manually login, open seahorse and change the Login keyring password.
Right click on "Login" and you will see a Change Password menu option.
To easily remember you could just use your user account password appended with a "k".

****NB**: Chromium based browsers use the Login keyring and may prompt to unlock if locked.

---

### Post by mIk3_08 on 2019-07-07
> **guber2 said:**
> The login keyring uses the same password as your login password.
To not unlock the keyring when you manually login, open seahorse and change the Login keyring password.
Right click on "Login" and you will see a Change Password menu option.
To easily remember you could just use your user account password appended with a "k".

****NB**: Chromium based browsers use the Login keyring and may prompt to unlock if locked.

My login keyring is already different from my login password. I've already change it since the time I used my online accounts. And I already set-up a basic password for my chrome browser so that it will no longer prompt any window asking for keyring. 

By the way thanks a lot guber2 for the response.

---

### Post by mIk3_08 on 2019-07-07
> **crip720 said:**
> Not quite sure what you are asking, if you don't want to put in password everytime you boot your computer you can just turn on automatic login in system settings(ubuntu unity).  This would cause the 'passwords and keys' app to stay lock until you put your password


Its security purpposes crip720. Thanks for the reply.

---

### Post by again? on 2019-07-07
If the password is different, after manually logging in you would be presented with an unlock prompt
when an application wants to access the keyring.
[ATTACH=CONFIG]283574[/ATTACH]

eg I just changed my keyring password and logged out.
Logging back in and looking at seahorse the Login keyring is still locked.
[ATTACH=CONFIG]283575[/ATTACH]

---

### Post by mIk3_08 on 2019-07-07
Yes. I've encountered that one on my browser opera and chrome but I've set-up a basic password of it to get rid of that login keyring pop window.

---

### Post by mIk3_08 on 2019-07-07
> **guber2 said:**
> If the password is different, after manually logging in you would be presented with an unlock prompt
when an application wants to access the keyring.
[ATTACH=CONFIG]283574[/ATTACH]

eg I just changed my keyring password and logged out.
Logging back in and looking at seahorse the Login keyring is still locked.
[ATTACH=CONFIG]283575[/ATTACH]



Here is what I do.... to solve the issue of my chrome and opera.
see image below;

[ATTACH=CONFIG]283576[/ATTACH]

---

### Post by again? on 2019-07-07
I am seeing some very odd behaviour here. (Xubuntu 18.04 with lightdm)
Maybe the way the login keyring behaves has been changed.
If I change the login keyring password and then logout with the keyring unlocked, the password
is changed back to my user password and the keyring is auto unlocked at next login????? :confused:

Seems that even if the keyring password is changed it will revert to your user login if the keyring
is unlocked when you logout. :shock:#-o
If the keyring is locked at logout, it will retain the changed password and not auto unlock at next login.

---

### Post by mIk3_08 on 2019-07-07
> **guber2 said:**
> I am seeing some very odd behaviour here. (Xubuntu 18.04 with lightdm)
Maybe the way the login keyring behaves has been changed.
If I change the login keyring password and then logout with the keyring unlocked, the password
is changed back to my user password and the keyring is auto unlocked at next login????? :confused:

Seems that even if the keyring password is changed it will revert to your user login if the keyring
is unlocked when you logout. :shock:#-o
If the keyring is locked at logout, it will retain the changed password and not auto unlock at next login.


I think this is closer to my issue. Unity Ubuntu 18.04 lightdm.
> If the keyring is locked at logout, it will retain the changed password and not auto unlock at next login.
But after a few logins, it will only back to the auto unlocked after a few next logins.
That's why I'm keeping it locked every time I login to my system. That's why I find ways to get rid of this.

---

### Post by again? on 2019-07-07
Why does it worry you that the keyring is unlocked at log in?
Not something that I have looked at but try a search for disabling or removing gnome-keyring.

---

### Post by mIk3_08 on 2019-07-08
> **guber2 said:**
> Why does it worry you that the keyring is unlocked at log in?
Not something that I have looked at but try a search for disabling or removing gnome-keyring.

> Why does it worry you that the keyring is unlocked at log in?

It's the security purposes. I know that you already knew that, It happens to me already that some of my web account password automatically stores to that login keyring; And it was very clear and I've witness it. It will automatically appear and it will vanish without even noticing it. so weird. 

> removing gnome-keyring
I think removing it, is not a solution. But thanks a lot for the concern and replies guber2.

---

### Post by again? on 2019-07-09
****Failing another solution I found this simple program to lock the keyring.
You need the dev package to compile.
```
sudo apt install libgnome-keyring-dev
```

Create directory and add the program...
```
mkdir ~/lock-keyring
gedit ~/lock-keyring/lock-keyring.c
```

Copy and paste the below code into **~/lock-keyring/lock-keyring.c** and save...
```
#include <stdio.h>
#include <gnome-keyring.h>

int main() {
    GnomeKeyringResult lock_result = gnome_keyring_lock_all_sync();
    if (lock_result == GNOME_KEYRING_RESULT_OK) {
        printf("Successfully locked\n");
        return 0;
    } else {
        printf("Error locking keyring: %d\n", lock_result);
        return 1;
    }
}
```

Compile...
```
cd ~/lock-keyring
cc lock-keyring.c -o lock-keyring -Wall $(pkg-config gnome-keyring-1 --cflags --libs)
```

Copy the compiled progam to your ~/bin directory.
```
mkdir ~/bin
cp ~/lock-keyring/lock-keyring ~/bin
```

Open seahorse, unlock the Login keyring and close seahorse. 
Test locking the Login keyring via terminal...
```
lock-keyring
```

Open seahorse and check if locked.
If that works add **lock-keyring** as the command in startup applications.

---

### Post by mIk3_08 on 2019-07-10
Okay guber2. I'll try this one. I'll get back to you for the feedback.

---

