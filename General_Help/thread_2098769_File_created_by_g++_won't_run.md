---
title: "File created by g++ won't run"
date: 2012-12-27
forum: General Help
---

### Post by trevhill on 2012-12-27
I can't get the executable created by g++ to execute. I run the command:

%: g++ test.cpp -o a.out

The file gets created, and objdump -d a.out seems to produce the correct assembly, but when I try this:

%: ./a.out

I get bash: ./a.out: Permission denied. I run it as sudo, and get sudo: ./a.out: command not found.

I copied the .cpp file with scp over to my school's linux server and follow the same steps, and everything works fine. When I scp the a.out file itself to the linux server, I get the same problem. However when I scp the a.out file that was working on the server to my computer, I still can't execute it.


#include <iostream>
using namespace std;

int main(){
   cout << "Hello" << endl;
}

---

### Post by windscape on 2012-12-27
Hi,

For a binary executable to execute, it must have the correct permissions assigned to it. Try the command: ```
chmod 755 a.out
```

If that doesn't work, show us the permissions of the file with the command: ```
ls -l a.out
```

---

### Post by steeldriver on 2012-12-27
Usually gcc / g++ create a.out with appropriate permissions - chmod shouldn't be necessary - if it's not executing then the most likely reason is that you are doing this on a filesystem that doesn't understand Linux permission bits (e.g. NTFS)

---

### Post by trevhill on 2012-12-27
Ok, so now my problem is I can't get chmod to work on a.out. After running:

%chmod 755 a.out   (also tried %sudo chmod 755 a.out)
%ls -l a.out

the output looks like this:

-rw------- 1 thill thill  9323 Dec 27 11:54 a.out

When I scp the a.out file to my server and do chmod 755, it works and runs. But when I scp the a.out from the server to my computer, chmod still won't change the permissions.

I created a dummy folder with a dummy file in it to see if chmod would work on it, get the same results when I try to chmod it.

Also, I am running on an ext4 filesystem.

---

### Post by trevhill on 2012-12-27
Figured it out, steel driver was right. I was in a shared partition between linux and windows, which is not ext4. I did everything within a folder on the ext4 file system, and everything works.

---

### Post by Topsiho on 2012-12-27
I repeated your steps in Ubuntu 12.04, without any problem, and got an executable a.out, with the correct permissions:

-rwxrwxr-x  1 jaap jaap  9097 dec 27 20:50 a.out

I did this in a directory in my home directory.

Thanks for teaching us how to disassemble this code using objdump :)

Topsiho

---

