---
title: "libpthread-dev broken dependency problem"
date: 2007-09-21
forum: General Help
---

### Post by capitol on 2007-09-21
Hi here is a dependecy problem i think, i just wanted to make sure before i report the error. in feisty

> 
$ sudo apt-get install libpthread-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-regex1.33.1 libflac++5c2 libsane libieee1284-3 libevent1 libboost-thread1.33.1 tsocks libicu34-dev libboost-filesystem1.33.1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libpthread20
The following NEW packages will be installed:
  libpthread-dev libpthread20
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 210kB of archives.
After unpacking 524kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/main libpthread20 2.0.7-4build1 [82.7kB]
Get:2 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/main libpthread-dev 2.0.7-4build1 [128kB]
Fetched 210kB in 1s (122kB/s)          
Selecting previously deselected package libpthread20.
(Reading database ... 147247 files and directories currently installed.)
Unpacking libpthread20 (from .../libpthread20_2.0.7-4build1_i386.deb) ...
Selecting previously deselected package libpthread-dev.
Unpacking libpthread-dev (from .../libpthread-dev_2.0.7-4build1_i386.deb) ...
Adding `diversion of /usr/include/pthread.h to /usr/include/pthread.h.glibc by libpthread-dev'
Adding `diversion of /usr/lib/libpthread.a to /usr/lib/libpthread.a.glibc by libpthread-dev'
Adding `diversion of /usr/lib/libpthread.so to /usr/lib/libpthread.so.glibc by libpthread-dev'
Setting up libpthread20 (2.0.7-4build1) ...

Setting up libpthread-dev (2.0.7-4build1) ...

$ gcc pthread1.c 
In file included from pthread1.c:3:
/usr/include/pthread.h:285: error: conflicting types for 'pthread_t'
/usr/include/bits/pthreadtypes.h:36: error: previous declaration of 'pthread_t' was here
/usr/include/pthread.h:286: error: conflicting types for 'pthread_attr_t'
/usr/include/bits/pthreadtypes.h:43: error: previous declaration of 'pthread_attr_t' was here
/usr/include/pthread.h:287: error: conflicting types for 'pthread_key_t'
/usr/include/bits/pthreadtypes.h:109: error: previous declaration of 'pthread_key_t' was here
/usr/include/pthread.h:289: error: conflicting types for 'pthread_mutexattr_t'
/usr/include/bits/pthreadtypes.h:79: error: previous declaration of 'pthread_mutexattr_t' was here
/usr/include/pthread.h:290: error: conflicting types for 'pthread_mutex_t'
/usr/include/bits/pthreadtypes.h:73: error: previous declaration of 'pthread_mutex_t' was here
/usr/include/pthread.h:291: error: conflicting types for 'pthread_condattr_t'
/usr/include/bits/pthreadtypes.h:105: error: previous declaration of 'pthread_condattr_t' was here
/usr/include/pthread.h:292: error: conflicting types for 'pthread_cond_t'
/usr/include/bits/pthreadtypes.h:99: error: previous declaration of 'pthread_cond_t' was here
/usr/include/pthread.h:293: error: conflicting types for 'pthread_rwlockattr_t'
/usr/include/bits/pthreadtypes.h:142: error: previous declaration of 'pthread_rwlockattr_t' was here
/usr/include/pthread.h:294: error: conflicting types for 'pthread_rwlock_t'
/usr/include/bits/pthreadtypes.h:136: error: previous declaration of 'pthread_rwlock_t' was here

> 
$ cat pthread1.c 
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>

void *print_message_function( void *ptr );

main()
{
  pthread_t thread1, thread2;
  char *message1 = "Thread 1";
  char *message2 = "Thread 2";
  int  iret1, iret2;

  /* Create independent threads each of which will execute function */

  iret1 = pthread_create( &thread1, NULL, print_message_function, (void*) message1);
  iret2 = pthread_create( &thread2, NULL, print_message_function, (void*) message2);

  /* Wait till threads are complete before main continues. Unless we  */
  /* wait we run the risk of executing an exit which will terminate   */
  /* the process and all threads before the threads have completed.   */

  pthread_join( thread1, NULL);
  pthread_join( thread2, NULL); 

  printf("Thread 1 returns: %d\n",iret1);
  printf("Thread 2 returns: %d\n",iret2);
  exit(0);
}

void *print_message_function( void *ptr )
{
  char *message;
  message = (char *) ptr;
  printf("%s \n", message);
}



---

### Post by ionel on 2007-10-23
I have the same errors when I want to compile a package.
did you resolve this ? how? 
Thanks in advance for help !

---

### Post by mmebane on 2007-11-11
I had similar problems.  You don't need libpthread-dev or libpthread20 to use pthreads, they just cause problems.  I think you just need libc6-dev.

---

