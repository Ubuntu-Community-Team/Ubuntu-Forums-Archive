---
title: "locate command copy all files"
date: 2022-03-07
forum: General Help
---

### Post by cmcanulty on 2022-03-07
I am trying to duplicate a very complicated app to a new computer and none of the prescribed fixes work. So I would like to copy all the files I find under the locate command to a ext drive from the computer where the app works to another computer and try it that way. So I type locate 'example' and then copy while still in the terminal
all the located files to a flash drive. Then I can paste them to another machine. Is this possible? I am aware this may cause problems in the new computer

---

### Post by SeijiSensei on 2022-03-07
This seemed to work for me:

```
cp $(locate some_string) some_directory
```

It copied every file with "some_string" in its name to the target directory.

The "$()" operator in bash runs the command inside the parentheses and returns any result. It has replaced the traditional "backtick" operator (`) in earlier shells. (Backticks still work, of course.)

---

### Post by dragonfly41 on 2022-03-07
Also run ldd on your app to find dependencies.
And run sudo updatedb before your run.
View the options in man locate.

P.S. first check permissions of dependencies before cloning.

---

### Post by TheFu on 2022-03-07
It depends on the software whether cp will be sufficient or not.
Why can't you just install it the same way you did on the other computer, then copy the settings (/etc/ and ~/.somewhere) over to the new system?

As others say, you'll need to handle any dependencies manually if you just cp files.  There may be none, but that is extremely unusual. Usually there are 5+ other packages for every program on a system. Without those dependencies installed, it won't work.  There are compiled libraries or if the program is a script, there can be 5-100 script packages it is dependent on.  

If you use a flash drive with exFAT or FAT32, you'll lose all owner, group, permissions, ACLs and xattrs that can be critical to the program working correctly.

BTW, locate doesn't find all the files, necessarily, for a package.

---

### Post by cmcanulty on 2022-03-07
it is a real complicated install with a lot of dependencies all of which I did. It works fine on computer 1 and will not install on computer 2. I am copying the install file from the terminal below. No amount of fiddling will put it on computer 2 which has exactly the same setup. it's a chess database program. The only reason I thought to copy all the scidb files found with locate to computer 2 is I have tried everything else I could think of including the tweak to /etc/sysctl.d/10-ptrace.conf changing the 1 to 0 in this line that was suggested in a help note

```
kernel.yama.ptrace_scope = 1

```
[https://sourceforge.net/projects/scidb/files/latest/download]("https://sourceforge.net/projects/scidb/files/latest/download")
```

cmcanulty@Asus:~/scidb-code-1475$ ./configure
configure: Makefile configuration program for Scidb
Renaming "Makefile.in" to "Makefile.in.bak"
    Tcl/Tk version: 8.6
    Your operating system is: Linux 5.13.0-30-generic
                 Distributor: Ubuntu
                    Revision: 20.04
                     Version: 20.04.4 LTS (Focal Fossa)
    Checking if your system has gcc installed: yes (version 9.4).
    Checking if your system has g++ installed: yes (version 9.4).
    Checking if your kernel supports __sync_* builtin functions: yes.
    Location of tcl.h: /usr/include/tcl8.6
    Location of tk.h: /usr/include/tcl8.6
    Location of Tcl 8.6 library: /usr/lib/x86_64-linux-gnu
    Location of Tk 8.6 library: /usr/lib/x86_64-linux-gnu
    Location of X11/Xlib.h: /usr/include
    Location of X11 library: /usr/lib/x86_64-linux-gnu
    Location of Xcursor library: /usr/lib/x86_64-linux-gnu
    Location of fontconfig library: /usr/lib/x86_64-linux-gnu
    Checking your fontconfig version: 2.13
    Checking if your system has X11/SM/SM.h: yes.
    Checking if your system has fontconfig: yes.
    Checking if your system has freetype2: yes.
    Checking if your kernel has inotify support: yes
    Checking if your system already has zlib installed: yes.
    Checking if your system already has zziplib installed: yes.
    Checking if your system already has expat installed: yes.
    Checking if your system already has gdbm installed: yes.
Makefile.in configured for your system was written.
Now just type "make" to compile Scidb.

IMPORTANT NOTE:
-------------------------------------------------------------------------------
The distributed Tk library may be broken, it is possible that some windows of
the application will freeze. In this case you have to use a self-compiled Tk
library if you want to avoid this problem (read INSTALL).

It is highly recommended to build Scidb on a working Unix system. This system
is broken and distorted due to the "kernel hardening" paranoia, which assumes
that every software is an attacker. But Scidb is definitively not an attacker
and requires a sane system.
cmcanulty@Asus:~/scidb-code-1475$ make
make[1]: 'scidb-beta.1.gz' is up to date.
Compiling db_consumer.cpp                 [-Wall -g -I/usr/include/tcl8.6 -DSCI_NAMEBASE_FIX=1]
In file included from ../mstl/m_bitset.h:266,
                 from db_annotation.h:34,
                 from db_consumer.cpp:29:
../mstl/m_bitset.ipp: In member function ‘void mstl::bitset::fill(mstl::bitset::size_type, mstl::bitset::size_type, unsigned char)’:
../mstl/m_bitset.ipp:385:66: warning: ‘void* memset(void*, int, size_t)’ writing to an object of non-trivial type ‘mstl::bitset::bitfield’ {aka ‘class mstl::bitfield<long unsigned int>’}; use assignment instead [-Wclass-memaccess]
  385 |  ::memset(m_bits + first, value, sizeof(m_bits[0])*(last - first));
      |                                                                  ^
In file included from db_common.h:32,
                 from db_provider.h:30,
                 from db_consumer.h:30,
                 from db_consumer.cpp:27:
../mstl/m_bitfield.h:25:7: note: ‘mstl::bitset::bitfield’ {aka ‘class mstl::bitfield<long unsigned int>’} declared here
   25 | class bitfield
      |       ^~~~~~~~
In file included from ../mstl/m_memblock.h:71,
                 from ../mstl/m_vector.h:24,
                 from db_move_info_set.h:34,
                 from db_consumer.h:34,
                 from db_consumer.cpp:27:
../mstl/m_memblock.ipp: In instantiation of ‘mstl::memblock<U>& mstl::memblock<T>::operator=(mstl::memblock<T>&&) [with T = db::Mark]’:
../mstl/m_vector.ipp:790:35:   required from ‘mstl::vector<T>& mstl::vector<T>::operator=(mstl::vector<T>&&) [with T = db::Mark]’
db_mark_set.ipp:124:34:   required from here
../mstl/m_memblock.ipp:134:22: error: no matching function for call to ‘mstl::memblock<db::Mark>::~memblock()’
  134 |   memblock::~memblock();
      |   ~~~~~~~~~~~~~~~~~~~^~
../mstl/m_memblock.ipp:45:1: note: candidate: ‘mstl::memblock<T>::~memblock() [with T = db::Mark]’
   45 | memblock<T>::~memblock() throw()
      | ^~~~~~~~~~~
../mstl/m_memblock.ipp:45:1: note:   candidate expects 1 argument, 0 provided
In file included from ../mstl/m_vector.h:189,
                 from db_move_info_set.h:34,
                 from db_consumer.h:34,
                 from db_consumer.cpp:27:
../mstl/m_vector.ipp: In instantiation of ‘void mstl::vector<T>::insert_aux(mstl::vector<T>::iterator, mstl::vector<T>::const_reference) [with T = mstl::pair<mstl::string, unsigned int>; mstl::vector<T>::iterator = mstl::pointer_iterator<mstl::pair<mstl::string, unsigned int> >; mstl::vector<T>::const_reference = const mstl::pair<mstl::string, unsigned int>&; mstl::vector<T>::value_type = mstl::pair<mstl::string, unsigned int>]’:
../mstl/m_vector.ipp:519:2:   required from ‘mstl::vector<T>::iterator mstl::vector<T>::insert(mstl::vector<T>::iterator, mstl::vector<T>::const_reference) [with T = mstl::pair<mstl::string, unsigned int>; mstl::vector<T>::iterator = mstl::pointer_iterator<mstl::pair<mstl::string, unsigned int> >; mstl::vector<T>::const_reference = const mstl::pair<mstl::string, unsigned int>&; mstl::vector<T>::value_type = mstl::pair<mstl::string, unsigned int>]’
../mstl/m_map.ipp:233:5:   required from ‘mstl::map<K, V>::mapped_type& mstl::map<K, V>::operator[](mstl::map<K, V>::const_key_ref) [with K = mstl::string; V = unsigned int; mstl::map<K, V>::mapped_type = unsigned int; mstl::map<K, V>::const_key_ref = const mstl::string&]’
db_consumer.cpp:147:24:   required from here
../mstl/m_vector.ipp:699:13: warning: ‘void* memmove(void*, const void*, size_t)’ writing to an object of type ‘mstl::pointer_iterator<mstl::pair<mstl::string, unsigned int> >::value_type’ {aka ‘class mstl::pair<mstl::string, unsigned int>’} with no trivial copy-assignment; use copy-assignment or copy-initialization instead [-Wclass-memaccess]
  699 |    ::memmove( pointer(position) + 1,
      |    ~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~
  700 |        pointer(position),
      |        ~~~~~~~~~~~~~~~~~~
  701 |        mstl::distance(position, end())*sizeof(value_type));
      |        ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In file included from ../mstl/m_map.h:23,
                 from db_engine_list.h:28,
                 from db_consumer.h:35,
                 from db_consumer.cpp:27:
../mstl/m_pair.h:25:7: note: ‘mstl::pointer_iterator<mstl::pair<mstl::string, unsigned int> >::value_type’ {aka ‘class mstl::pair<mstl::string, unsigned int>’} declared here
   25 | class pair
      |       ^~~~
In file included from ../mstl/m_uninitialized.h:56,
                 from ../mstl/m_vector.ipp:19,
                 from ../mstl/m_vector.h:189,
                 from db_move_info_set.h:34,
                 from db_consumer.h:34,
                 from db_consumer.cpp:27:
../mstl/m_uninitialized.ipp: In instantiation of ‘static T* mstl::bits::uninitialized_pod<NBytes>::copy(InputIterator, InputIterator, T*) [with InputIterator = mstl::pair<mstl::string, unsigned int>*; T = mstl::pair<mstl::string, unsigned int>; long unsigned int NBytes = 32]’:
../mstl/m_uninitialized.ipp:95:44:   required from ‘static T* mstl::bits::uninitialized<1>::copy(InputIterator, InputIterator, T*) [with InputIterator = mstl::pair<mstl::string, unsigned int>*; T = mstl::pair<mstl::string, unsigned int>]’
../mstl/m_uninitialized.ipp:158:56:   required from ‘T* mstl::uninitialized_move(T*, T*, T*) [with T = mstl::pair<mstl::string, unsigned int>]’
../mstl/m_vector.ipp:409:43:   required from ‘void mstl::vector<T>::reserve(mstl::vector<T>::size_type) [with T = mstl::pair<mstl::string, unsigned int>; mstl::vector<T>::size_type = long unsigned int]’
../mstl/m_map.ipp:32:80:   required from ‘void mstl::map<K, V>::reserve(mstl::map<K, V>::size_type) [with K = mstl::string; V = unsigned int; mstl::map<K, V>::size_type = long unsigned int]’
db_engine_list.ipp:36:69:   required from here
../mstl/m_uninitialized.ipp:60:12: warning: ‘void* memmove(void*, const void*, size_t)’ writing to an object of type ‘class mstl::pair<mstl::string, unsigned int>’ with no trivial copy-assignment; use copy-assignment or copy-initialization instead [-Wclass-memaccess]
   60 |   ::memmove(result, first, NBytes*(last - first));
      |   ~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In file included from ../mstl/m_map.h:23,
                 from db_engine_list.h:28,
                 from db_consumer.h:35,
                 from db_consumer.cpp:27:
../mstl/m_pair.h:25:7: note: ‘class mstl::pair<mstl::string, unsigned int>’ declared here
   25 | class pair
      |       ^~~~
In file included from ../mstl/m_uninitialized.h:56,
                 from ../mstl/m_vector.ipp:19,
                 from ../mstl/m_vector.h:189,
                 from db_move_info_set.h:34,
                 from db_consumer.h:34,
                 from db_consumer.cpp:27:
../mstl/m_uninitialized.ipp: In instantiation of ‘static T* mstl::bits::uninitialized_pod<NBytes>::copy(InputIterator, InputIterator, T*) [with InputIterator = mstl::string*; T = mstl::string; long unsigned int NBytes = 24]’:
../mstl/m_uninitialized.ipp:95:44:   required from ‘static T* mstl::bits::uninitialized<1>::copy(InputIterator, InputIterator, T*) [with InputIterator = mstl::string*; T = mstl::string]’
../mstl/m_uninitialized.ipp:158:56:   required from ‘T* mstl::uninitialized_move(T*, T*, T*) [with T = mstl::string]’
../mstl/m_vector.ipp:409:43:   required from ‘void mstl::vector<T>::reserve(mstl::vector<T>::size_type) [with T = mstl::string; mstl::vector<T>::size_type = long unsigned int]’
../mstl/m_vector.ipp:310:3:   required from ‘mstl::vector<T>& mstl::vector<T>::operator=(const mstl::vector<T>&) [with T = mstl::string]’
db_consumer.cpp:83:24:   required from here
../mstl/m_uninitialized.ipp:60:12: warning: ‘void* memmove(void*, const void*, size_t)’ writing to an object of type ‘class mstl::string’ with no trivial copy-assignment; use copy-assignment or copy-initialization instead [-Wclass-memaccess]
   60 |   ::memmove(result, first, NBytes*(last - first));
      |   ~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In file included from db_move.h:38,
                 from db_move_list.h:30,
                 from db_board.h:34,
                 from db_consumer.h:31,
                 from db_consumer.cpp:27:
../mstl/m_string.h:28:7: note: ‘class mstl::string’ declared here
   28 | class string
      |       ^~~~~~
make[2]: *** [Makefile:162: db_consumer.o] Error 1
make[1]: *** [Makefile:205: recursive] Error 1
make: *** [Makefile:20: all] Error 2
cmcanulty@Asus:~/scidb-code-1475$ make install
Install man pages
install: cannot remove '/usr/local/man/man1/scidb-beta.1.gz': Permission denied
make[1]: *** [Makefile:31: install] Error 1
make: *** [Makefile:86: install-subdirs] Error 2
cmcanulty@Asus:~/scidb-code-1475$ sudo make install
[sudo] password for cmcanulty: 
Install man pages
Compiling db_consumer.cpp                 [-Wall -g -I/usr/include/tcl8.6 -DSCI_NAMEBASE_FIX=1]
In file included from ../mstl/m_bitset.h:266,
                 from db_annotation.h:34,
                 from db_consumer.cpp:29:
../mstl/m_bitset.ipp: In member function ‘void mstl::bitset::fill(mstl::bitset::size_type, mstl::bitset::size_type, unsigned char)’:
../mstl/m_bitset.ipp:385:66: warning: ‘void* memset(void*, int, size_t)’ writing to an object of non-trivial type ‘mstl::bitset::bitfield’ {aka ‘class mstl::bitfield<long unsigned int>’}; use assignment instead [-Wclass-memaccess]
  385 |  ::memset(m_bits + first, value, sizeof(m_bits[0])*(last - first));
      |                                                                  ^
In file included from db_common.h:32,
                 from db_provider.h:30,
                 from db_consumer.h:30,
                 from db_consumer.cpp:27:
../mstl/m_bitfield.h:25:7: note: ‘mstl::bitset::bitfield’ {aka ‘class mstl::bitfield<long unsigned int>’} declared here
   25 | class bitfield
      |       ^~~~~~~~
In file included from ../mstl/m_memblock.h:71,
                 from ../mstl/m_vector.h:24,
                 from db_move_info_set.h:34,
                 from db_consumer.h:34,
                 from db_consumer.cpp:27:
../mstl/m_memblock.ipp: In instantiation of ‘mstl::memblock<U>& mstl::memblock<T>::operator=(mstl::memblock<T>&&) [with T = db::Mark]’:
../mstl/m_vector.ipp:790:35:   required from ‘mstl::vector<T>& mstl::vector<T>::operator=(mstl::vector<T>&&) [with T = db::Mark]’
db_mark_set.ipp:124:34:   required from here
../mstl/m_memblock.ipp:134:22: error: no matching function for call to ‘mstl::memblock<db::Mark>::~memblock()’
  134 |   memblock::~memblock();
      |   ~~~~~~~~~~~~~~~~~~~^~
../mstl/m_memblock.ipp:45:1: note: candidate: ‘mstl::memblock<T>::~memblock() [with T = db::Mark]’
   45 | memblock<T>::~memblock() throw()
      | ^~~~~~~~~~~
../mstl/m_memblock.ipp:45:1: note:   candidate expects 1 argument, 0 provided
In file included from ../mstl/m_vector.h:189,
                 from db_move_info_set.h:34,
                 from db_consumer.h:34,
                 from db_consumer.cpp:27:
../mstl/m_vector.ipp: In instantiation of ‘void mstl::vector<T>::insert_aux(mstl::vector<T>::iterator, mstl::vector<T>::const_reference) [with T = mstl::pair<mstl::string, unsigned int>; mstl::vector<T>::iterator = mstl::pointer_iterator<mstl::pair<mstl::string, unsigned int> >; mstl::vector<T>::const_reference = const mstl::pair<mstl::string, unsigned int>&; mstl::vector<T>::value_type = mstl::pair<mstl::string, unsigned int>]’:
../mstl/m_vector.ipp:519:2:   required from ‘mstl::vector<T>::iterator mstl::vector<T>::insert(mstl::vector<T>::iterator, mstl::vector<T>::const_reference) [with T = mstl::pair<mstl::string, unsigned int>; mstl::vector<T>::iterator = mstl::pointer_iterator<mstl::pair<mstl::string, unsigned int> >; mstl::vector<T>::const_reference = const mstl::pair<mstl::string, unsigned int>&; mstl::vector<T>::value_type = mstl::pair<mstl::string, unsigned int>]’
../mstl/m_map.ipp:233:5:   required from ‘mstl::map<K, V>::mapped_type& mstl::map<K, V>::operator[](mstl::map<K, V>::const_key_ref) [with K = mstl::string; V = unsigned int; mstl::map<K, V>::mapped_type = unsigned int; mstl::map<K, V>::const_key_ref = const mstl::string&]’
db_consumer.cpp:147:24:   required from here
../mstl/m_vector.ipp:699:13: warning: ‘void* memmove(void*, const void*, size_t)’ writing to an object of type ‘mstl::pointer_iterator<mstl::pair<mstl::string, unsigned int> >::value_type’ {aka ‘class mstl::pair<mstl::string, unsigned int>’} with no trivial copy-assignment; use copy-assignment or copy-initialization instead [-Wclass-memaccess]
  699 |    ::memmove( pointer(position) + 1,
      |    ~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~
  700 |        pointer(position),
      |        ~~~~~~~~~~~~~~~~~~
  701 |        mstl::distance(position, end())*sizeof(value_type));
      |        ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In file included from ../mstl/m_map.h:23,
                 from db_engine_list.h:28,
                 from db_consumer.h:35,
                 from db_consumer.cpp:27:
../mstl/m_pair.h:25:7: note: ‘mstl::pointer_iterator<mstl::pair<mstl::string, unsigned int> >::value_type’ {aka ‘class mstl::pair<mstl::string, unsigned int>’} declared here
   25 | class pair
      |       ^~~~
In file included from ../mstl/m_uninitialized.h:56,
                 from ../mstl/m_vector.ipp:19,
                 from ../mstl/m_vector.h:189,
                 from db_move_info_set.h:34,
                 from db_consumer.h:34,
                 from db_consumer.cpp:27:
../mstl/m_uninitialized.ipp: In instantiation of ‘static T* mstl::bits::uninitialized_pod<NBytes>::copy(InputIterator, InputIterator, T*) [with InputIterator = mstl::pair<mstl::string, unsigned int>*; T = mstl::pair<mstl::string, unsigned int>; long unsigned int NBytes = 32]’:
../mstl/m_uninitialized.ipp:95:44:   required from ‘static T* mstl::bits::uninitialized<1>::copy(InputIterator, InputIterator, T*) [with InputIterator = mstl::pair<mstl::string, unsigned int>*; T = mstl::pair<mstl::string, unsigned int>]’
../mstl/m_uninitialized.ipp:158:56:   required from ‘T* mstl::uninitialized_move(T*, T*, T*) [with T = mstl::pair<mstl::string, unsigned int>]’
../mstl/m_vector.ipp:409:43:   required from ‘void mstl::vector<T>::reserve(mstl::vector<T>::size_type) [with T = mstl::pair<mstl::string, unsigned int>; mstl::vector<T>::size_type = long unsigned int]’
../mstl/m_map.ipp:32:80:   required from ‘void mstl::map<K, V>::reserve(mstl::map<K, V>::size_type) [with K = mstl::string; V = unsigned int; mstl::map<K, V>::size_type = long unsigned int]’
db_engine_list.ipp:36:69:   required from here
../mstl/m_uninitialized.ipp:60:12: warning: ‘void* memmove(void*, const void*, size_t)’ writing to an object of type ‘class mstl::pair<mstl::string, unsigned int>’ with no trivial copy-assignment; use copy-assignment or copy-initialization instead [-Wclass-memaccess]
   60 |   ::memmove(result, first, NBytes*(last - first));
      |   ~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In file included from ../mstl/m_map.h:23,
                 from db_engine_list.h:28,
                 from db_consumer.h:35,
                 from db_consumer.cpp:27:
../mstl/m_pair.h:25:7: note: ‘class mstl::pair<mstl::string, unsigned int>’ declared here
   25 | class pair
      |       ^~~~
In file included from ../mstl/m_uninitialized.h:56,
                 from ../mstl/m_vector.ipp:19,
                 from ../mstl/m_vector.h:189,
                 from db_move_info_set.h:34,
                 from db_consumer.h:34,
                 from db_consumer.cpp:27:
../mstl/m_uninitialized.ipp: In instantiation of ‘static T* mstl::bits::uninitialized_pod<NBytes>::copy(InputIterator, InputIterator, T*) [with InputIterator = mstl::string*; T = mstl::string; long unsigned int NBytes = 24]’:
../mstl/m_uninitialized.ipp:95:44:   required from ‘static T* mstl::bits::uninitialized<1>::copy(InputIterator, InputIterator, T*) [with InputIterator = mstl::string*; T = mstl::string]’
../mstl/m_uninitialized.ipp:158:56:   required from ‘T* mstl::uninitialized_move(T*, T*, T*) [with T = mstl::string]’
../mstl/m_vector.ipp:409:43:   required from ‘void mstl::vector<T>::reserve(mstl::vector<T>::size_type) [with T = mstl::string; mstl::vector<T>::size_type = long unsigned int]’
../mstl/m_vector.ipp:310:3:   required from ‘mstl::vector<T>& mstl::vector<T>::operator=(const mstl::vector<T>&) [with T = mstl::string]’
db_consumer.cpp:83:24:   required from here
../mstl/m_uninitialized.ipp:60:12: warning: ‘void* memmove(void*, const void*, size_t)’ writing to an object of type ‘class mstl::string’ with no trivial copy-assignment; use copy-assignment or copy-initialization instead [-Wclass-memaccess]
   60 |   ::memmove(result, first, NBytes*(last - first));
      |   ~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In file included from db_move.h:38,
                 from db_move_list.h:30,
                 from db_board.h:34,
                 from db_consumer.h:31,
                 from db_consumer.cpp:27:
../mstl/m_string.h:28:7: note: ‘class mstl::string’ declared here
   28 | class string
      |       ^~~~~~
make[2]: *** [Makefile:162: db_consumer.o] Error 1
make[1]: *** [Makefile:205: recursive] Error 1
make: *** [Makefile:87: install-subdirs] Error 2
cmcanulty@Asus:~/scidb-code-1475$ 
```

---

### Post by dragonfly41 on 2022-03-07
This does not install?

[http://scidb.sourceforge.net/download.html](http://scidb.sourceforge.net/download.html)

---

### Post by cmcanulty on 2022-03-08
No, I put the terminal output in my previous post

---

### Post by dragonfly41 on 2022-03-08
Reading that installation page I see this note:

[SIZE=1]> [COLOR=#000000][FONT=Verdana]In case of errors in the installation descriptions, please report to [/FONT][/COLOR][EMAIL="gcramer@users.sourceforge.net"]gcramer@users.sourceforge.net[/EMAIL][COLOR=#000000][FONT=Verdana].

Perhaps the developer can help you?[/FONT][/COLOR][/SIZE]

---

### Post by TheFu on 2022-03-08
Appears the system is missing some dependencies. Fix those.

---

### Post by cmcanulty on 2022-03-08
I did install all the dependencies that were recommended am I missing something? I looked through the file and also searched for the words error or depend and got nothing. Thank you

---

### Post by TheFu on 2022-03-08
> **cmcanulty said:**
> I did install all the dependencies that were recommended am I missing something? Thank you

appears the wrong version of mstl got installed.  I didn't look too close.  In getting the right versions of libraries, we have to be 2 version level correct, so there is a little wiggle room. I'm assuming all those dependencies are using semantic version numbers.

So, if the version is 1.2.3, then any version of 1.2.x should be fine.  
When the 'y' changes in x.y.z, that means functions have changed.  
When  the 'x' changes, that means interfaces are broken.
When 'z' changes, that means some bug fix happened that _shouldn't_ impact any outside  use.

---

### Post by cmcanulty on 2022-03-08
how can I run ldd on the app when it won't install? I did do updatedb

---

### Post by cmcanulty on 2022-03-08
I can't find mstl in synaptic or with a google search to install and it doesn't show in synaptic as installed

---

### Post by dragonfly41 on 2022-03-08
The idea was to run ldd on the working app you referred to (which you are trying to clone).

Meanwhile doing something like this *should *show which dependencies are installed. Status.
Package list taken from earlier site.

dpkg -s /
libexpat1-dev /
libfontconfig1-dev /
libfreetype6-dev /
libxft-dev /
libxcursor-dev tcl8.5 /
tcl8.5-dev / 
tk8.5 /
tk8.5-dev /
zlib1g-dev /
libudev-dev /
libgdbm-dev /
libzzip-dev | grep Status


[Added note]

Another idea if you have Synaptic Package Manager.

Open GUI
Select Installed (manually)
Select Status


And if you know the _installed_ date of the working app (perhaps get date from properties?)

in Synaptic select Toolbar > File > History

and go to date of successful installation of the working app.

---

### Post by cmcanulty on 2022-03-08
OK thanks so much. I have to leave for work but will try all that when I get home

---

### Post by TheFu on 2022-03-08
> **cmcanulty said:**
> how can I run ldd on the app when it won't install? I did do updatedb

Someone reported that it is installed and working on the other machine. Run ldd there.

---

### Post by cmcanulty on 2022-03-08
Fixed!!! I did what crazy people do and tried install again for the umteenth time and this time it kicked out a new command to do bewteen ./configure and make. It said try make clean and presto it installed. Thanks for all the advice , solved.

---

### Post by dragonfly41 on 2022-03-08
Check mate

---

### Post by TheFu on 2022-03-08
> **cmcanulty said:**
> Fixed!!! I did what crazy people do and tried install again for the umteenth time and this time it kicked out a new command to do bewteen ./configure and make. It said try make clean and presto it installed. Thanks for all the advice , solved.

make is smart, but dumb.  It looks for the existence of files and the timestamp of those files. It doesn't know if a left-over, bad, file was the result of a prior attempt.

There are a few extremely common "targets" for a Makefile.

When we type 'make' with no argument, the default (1st) target is used. This is typically the most convenient for the developers.
There are usually targets in a Makefile for 'all', 'install', 'clean', 'cleanall', 'docs', and sometimes 'depend'.  The names for a target can be anything the Makefile creator likes. Often, the program name, library names, documentation, web-assets, and package are in there too, but it is completely up to the Makefile creator.  There are default targets that don't have to be specified in the makefile too - so a simple .c file can be compiled into a .o file.

When having dependency issues, it is best to run **make clean** between each attempt. That will usually remove any .o files based on the source files listed in the Makefile.  Makefile and makefile are the same. Either is assumed. Other names can be use with a -f argument to make.   **make -f ./some-other-makef**.

make (really gmake) has an extensive language and macros with assignments and pattern replacements.  Just know that Makefiles are {tab} sensitive.  Tab characters are mandatory in specific places, so if an editor replaces a tab with X spaces automatically, that will break the Makefile.  Targets must start in column 1.  Commands to fulfill those targets must have a leading {tab} - at least 1, but more are allowed without impacting the resulting parsing.

I'm sure there are better summaries of what's important in a makefile, but that's all that I recall off the top of my head now.

---

### Post by cmcanulty on 2022-03-08
Thanks I am saving your make write up as it is very clear and all new to me

---

