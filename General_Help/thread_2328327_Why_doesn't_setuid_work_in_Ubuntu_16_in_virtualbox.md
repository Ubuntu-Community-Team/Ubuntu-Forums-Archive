---
title: "Why doesn't setuid work in Ubuntu 16 in virtualbox?"
date: 2016-06-20
forum: General Help
---

### Post by trent9 on 2016-06-20
I have a small c++ program that executes a few system() commands.  In Ubuntu 14.04 everything works--I can set the owner as root and set  the setuid attribute and then anyone can run it with root permissions.

  ```
ls -l ./myprogram
-rwsrwxrwx 1 root root 19416 Dec 17  2015 myprogram
./myprogram # ... works

```  But when I run the exact same thing in Ubuntu 16 in virtualbox, I get permission denied in the system calls.
  ```
ls -l ./myprogram
-rwsrwxrwx 1 root root 19416 Dec 17  2015 myprogram
./myprogram # ... permission denied

```  If I run
  ```
sudo ./myprogram

```  in Ubuntu 16 then it works, but the setuid attribute is apparently being ignored for some reason. I can't figure out why. I ran mount to check that nosuid wasn't set for the filesystem, but it doesn't look like that is the problem. It gives me:
  /dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)

  The C++ program looks like:
  ```
#include <cstdlib>
#include <iostream>
#include "HwInfo.h"
#include <sys/types.h>
#include <unistd.h>

using namespace std;

static uid_t euid, ruid;

// Restore the effective uuid to its original value
void do_setuid (void) {
    int status;
#ifdef _POSIX_SAVED_IDS
    status = seteuid (euid);
#else
    status = setreuid (ruid, euid);
#endif
    if (status < 0) {
        //Couldn't set uid
        std::cerr << "Couldn't restore uid.";
        exit(status);
    }
}


// Set the effective UID to the real UID.
void undo_setuid (void) {
    int status;
#ifdef _POSIX_SAVED_IDS
    status = seteuid (ruid);
#else
    status = setreuid (euid, ruid);
#endif
    if (status < 0) {
        //Couldn't set uid
        std::cerr << "Couldn't set uid.";
        exit(status);
    }
}



int main(int argc, char** argv) {
    // Get the real and effective user ids
    ruid = getuid ();
    euid = geteuid ();
    do_setuid();

    system("some system commands");

    undo_setuid();
    return 0;
}
```

---

