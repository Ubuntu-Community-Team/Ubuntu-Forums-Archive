---
title: "boost and scons  Need help"
date: 2008-03-12
forum: General Help
---

### Post by dravidan on 2008-03-12
Trying to install dicomlib which uses boost libraries but I am having problems using scons to build the dicomlib libraries.  
Here is my error:

scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
o AssociationRejection.o -c -I/tmp -I/usr/lib/boost_1_31_0 AssociationRejection.cpp
sh: o: not found
o Buffer.o -c -I/tmp -I/usr/lib/boost_1_31_0 Buffer.cpp
sh: o: not found
o Cdimse.o -c -I/tmp -I/usr/lib/boost_1_31_0 Cdimse.cpp
sh: o: not found
o ClientConnection.o -c -I/tmp -I/usr/lib/boost_1_31_0 ClientConnection.cpp
sh: o: not found
o CommandSets.o -c -I/tmp -I/usr/lib/boost_1_31_0 CommandSets.cpp
sh: o: not found
o DataDictionary.o -c -I/tmp -I/usr/lib/boost_1_31_0 DataDictionary.cpp
sh: o: not found
o Decoder.o -c -I/tmp -I/usr/lib/boost_1_31_0 Decoder.cpp
sh: o: not found
o Dumper.o -c -I/tmp -I/usr/lib/boost_1_31_0 Dumper.cpp
sh: o: not found
o Encoder.o -c -I/tmp -I/usr/lib/boost_1_31_0 Encoder.cpp
sh: o: not found
o Exceptions.o -c -I/tmp -I/usr/lib/boost_1_31_0 Exceptions.cpp
sh: o: not found
o File.o -c -I/tmp -I/usr/lib/boost_1_31_0 File.cpp
sh: o: not found
o FileMetaInformation.o -c -I/tmp -I/usr/lib/boost_1_31_0 FileMetaInformation.cpp
sh: o: not found
o GroupLength.o -c -I/tmp -I/usr/lib/boost_1_31_0 GroupLength.cpp
sh: o: not found
o Ndimse.o -c -I/tmp -I/usr/lib/boost_1_31_0 Ndimse.cpp
sh: o: not found
o PresentationContexts.o -c -I/tmp -I/usr/lib/boost_1_31_0 PresentationContexts.cpp
sh: o: not found
o QueryRetrieve.o -c -I/tmp -I/usr/lib/boost_1_31_0 QueryRetrieve.cpp
sh: o: not found
o Server.o -c -I/tmp -I/usr/lib/boost_1_31_0 Server.cpp
sh: o: not found
o ServiceBase.o -c -I/tmp -I/usr/lib/boost_1_31_0 ServiceBase.cpp
sh: o: not found
o ThreadSpecificServer.o -c -I/tmp -I/usr/lib/boost_1_31_0 ThreadSpecificServer.cpp
sh: o: not found
o TransferSyntax.o -c -I/tmp -I/usr/lib/boost_1_31_0 TransferSyntax.cpp
sh: o: not found
o UID.o -c -I/tmp -I/usr/lib/boost_1_31_0 UID.cpp
sh: o: not found
o Utility.o -c -I/tmp -I/usr/lib/boost_1_31_0 Utility.cpp
sh: o: not found
o ValueToStream.o -c -I/tmp -I/usr/lib/boost_1_31_0 ValueToStream.cpp
sh: o: not found
o Version.o -c -I/tmp -I/usr/lib/boost_1_31_0 Version.cpp
sh: o: not found
o aaac.o -c -I/tmp -I/usr/lib/boost_1_31_0 aaac.cpp
sh: o: not found
o aarj.o -c -I/tmp -I/usr/lib/boost_1_31_0 aarj.cpp
sh: o: not found
o aarq.o -c -I/tmp -I/usr/lib/boost_1_31_0 aarq.cpp
sh: o: not found
o pdata.o -c -I/tmp -I/usr/lib/boost_1_31_0 pdata.cpp
sh: o: not found
ar rc libdicom.a aaac.o aarj.o aarq.o AssociationRejection.o Buffer.o Cdimse.o ClientConnection.o CommandSets.o DataDictionary.o Decoder.o Dumper.o Encoder.o Exceptions.o File.o FileMetaInformation.o GroupLength.o Ndimse.o pdata.o PresentationContexts.o QueryRetrieve.o Server.o ServiceBase.o ThreadSpecificServer.o TransferSyntax.o UID.o Utility.o ValueToStream.o Version.o
ar: aaac.o: No such file or directory
scons: *** [libdicom.a] Error 1
scons: building terminated because of errors.

I download and compiled boost form boost.org installed on /usr/lib/boost_1_34_1

This the SConstruct file:
import os
sources="""
        aaac.cpp
        aarj.cpp
        aarq.cpp
        AssociationRejection.cpp
        Buffer.cpp
        Cdimse.cpp
        ClientConnection.cpp
        CommandSets.cpp
        DataDictionary.cpp
        Decoder.cpp
        Dumper.cpp
        Encoder.cpp
        Exceptions.cpp
        File.cpp
        FileMetaInformation.cpp
        GroupLength.cpp
        Ndimse.cpp
        pdata.cpp
        PresentationContexts.cpp
        QueryRetrieve.cpp
        Server.cpp
        ServiceBase.cpp
        ThreadSpecificServer.cpp
        TransferSyntax.cpp
        UID.cpp
        Utility.cpp
        ValueToStream.cpp
        Version.cpp
"""

mylibs='/usr/lib'
boost_libs=mylibs+ '/boost_1_34_1'


cpppath=['..']
cpppath.append(mylibs + '/boost_1_31_0')
env = Environment(CPPPATH=cpppath,ENV = {'PATH' : os.environ['PATH']},LINK='g++')

env.StaticLibrary(target = 'dicom', source = sources.split())


$PATH gives the following:
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: No such file or directory

---

### Post by johnnyg on 2008-03-28
I just ran into this problem with scons.

In my case the problem was not having g++ installed.

sudo aptitude install g++

and all was well.

---

