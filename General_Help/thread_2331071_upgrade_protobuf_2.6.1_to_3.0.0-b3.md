---
title: "upgrade protobuf 2.6.1 to 3.0.0-b3?"
date: 2016-07-18
forum: General Help
---

### Post by jiapei100 on 2016-07-18
Hi, all::

I'm testing tensorlow, which is based on protobuf 3.0.0-b3/30.0-b2. But current Ubuntu 16.04 repository comes with protobuf 2.6.1 ... So when I tested my tensorflow code, I run into this error message:

[HTML][libprotobuf FATAL google/protobuf/stubs/common.cc:61] This program requires version 3.0.0 of the Protocol Buffer runtime library, but the installed version is 2.6.1.  Please update your library.  If you compiled the program yourself, make sure that your headers are from the same version of Protocol Buffers as your link-time library.  (Version verification failed in "external/protobuf/src/google/protobuf/any.pb.cc".)
terminate called after throwing an instance of 'google::protobuf::FatalException'
  what():  This program requires version 3.0.0 of the Protocol Buffer runtime library, but the installed version is 2.6.1.  Please update your library.  If you compiled the program yourself, make sure that your headers are from the same version of Protocol Buffers as your link-time library.  (Version verification failed in "external/protobuf/src/google/protobuf/any.pb.cc".)
Aborted (core dumped)[/HTML]

I wonder how to solve this protobuf version conflict issues?

Cheers
Pei

---

