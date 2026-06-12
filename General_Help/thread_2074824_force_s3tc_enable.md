---
title: "force_s3tc_enable"
date: 2012-10-22
forum: General Help
---

### Post by ajgreeny on 2012-10-22
I am getting the repeated error 
```
ATTENTION: default value of option force_s3tc_enable overridden by environment.
OS Determining best projection for type int (size:  4 ) signed
OS Projected as a regular number
OS Determining best projection for type unsigned_int (size:  4 ) unsigned
OS Projected as a regular number
OS Determining best projection for type long (size:  4 ) signed
OS Projected as a regular number
OS Determining best projection for type int (size:  4 ) signed
OS Projected as a regular number
OS Determining best projection for type int (size:  4 ) signed
OS Projected as a regular number
OS Determining best projection for type off_t (size:  4 ) signed
OS Projected as a large signed integer
OS Determining best projection for type size_t (size:  4 ) unsigned
OS Projected as a large unsigned integer
OS Determining best projection for type ssize_t (size:  4 ) signed
OS Projected as a large signed integer
OS Unix Could not open libc libsystem.B.dylib
OS Unix dirent is: ctypes.StructType("dirent", [{ "padding_0": ctypes.uint8_t.array(10) }, { "d_type": ctypes.uint8_t }, { "d_name": ctypes.char.array(257) }])
OS Attempting to declare FFI  access
OS Function access declared
OS Attempting to declare FFI  chdir
OS Function chdir declared
OS Attempting to declare FFI  chmod
OS Function chmod declared
OS Attempting to declare FFI  chown
OS Function chown declared
OS Attempting to declare FFI  copyfile
OS Could not declare function copyfile Error: couldn't find function symbol in library
OS Attempting to declare FFI  dup
OS Function dup declared
OS Attempting to declare FFI  chdir
OS Function chdir declared
OS Attempting to declare FFI  fchdir
OS Function fchdir declared
OS Attempting to declare FFI  fchown
OS Function fchown declared
OS Attempting to declare FFI  fsync
OS Function fsync declared
OS Attempting to declare FFI  getcwd
OS Function getcwd declared
OS Attempting to declare FFI  getwd
OS Function getwd declared
OS Attempting to declare FFI  get_current_dir_name
OS Function get_current_dir_name declared
OS Attempting to declare FFI  getwd
OS Function getwd declared
OS Attempting to declare FFI  fdatasync
OS Function fdatasync declared
OS Attempting to declare FFI  ftruncate
OS Function ftruncate declared
OS Attempting to declare FFI  lchown
OS Function lchown declared
OS Attempting to declare FFI  link
OS Function link declared
OS Attempting to declare FFI  lseek
OS Function lseek declared
OS Attempting to declare FFI  mkdir
OS Function mkdir declared
OS Attempting to declare FFI  mkstemp
OS Function mkstemp declared
OS Attempting to declare FFI  open
OS Function open declared
OS Attempting to declare FFI  opendir
OS Function opendir declared
OS Attempting to declare FFI  pread
OS Function pread declared
OS Attempting to declare FFI  pwrite
OS Function pwrite declared
OS Attempting to declare FFI  read
OS Function read declared
OS Attempting to declare FFI  readdir
OS Function readdir declared
OS Attempting to declare FFI  rename
OS Function rename declared
OS Attempting to declare FFI  rmdir
OS Function rmdir declared
OS Attempting to declare FFI  splice
OS Function splice declared
OS Attempting to declare FFI  strerror
OS Function strerror declared
OS Attempting to declare FFI  symlink
OS Function symlink declared
OS Attempting to declare FFI  truncate
OS Function truncate declared
OS Attempting to declare FFI  unlink
OS Function unlink declared
OS Attempting to declare FFI  write
OS Function write declared
OS Attempting to declare FFI  pipe
OS Function pipe declared

```All my searches point to a number of games being the culprit, mainly **planeshift** but I am not a gamer, and have not used any games that I have seen referenced.

Anyone got any idea where this error is coming from?

---

### Post by ajgreeny on 2012-12-16
I am adding this post to the thread just in case anyone else sees the problem in future.
In my case it has been solved purely by normal updates.
I accidentally found that the lines in xsession-errors appeared when I started or closed Firefox 15, which is the version that was around on the thread's date, 22 Oct.  The new versions of FF have stopped the error message appearing.

---

