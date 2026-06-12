---
title: "wxMusik"
date: 2005-06-13
forum: General Help
---

### Post by Jamesia on 2005-06-13
I've been trying to compile wxMusik. I thought I found all the requirements and installed them, but once I get down to compiling wxMusik itself, I get the following error:

```
Building executable /home/sammy/Desktop/wxMusik-0.4.1.0/crelbuild/wxMusik...
/home/sammy/musik/libMUSIKEngine.a(mpcdecoder.o)(.text+0x5a): In function `MUSIKMPCDecoder::MUSIKMPCDecoder[not-in-charge](IMUSIKStreamOut*)':
/home/sammy/Desktop/wxMusik-0.4.1.0/MUSIKEngine/MUSIKEngine/src/mpcdecoder.cpp:31: undefined reference to `StreamInfo::StreamInfo[in-charge]()'
/home/sammy/musik/libMUSIKEngine.a(mpcdecoder.o)(.text+0x11a): In function `MUSIKMPCDecoder::MUSIKMPCDecoder[in-charge](IMUSIKStreamOut*)':
/home/sammy/Desktop/wxMusik-0.4.1.0/MUSIKEngine/MUSIKEngine/src/mpcdecoder.cpp:31: undefined reference to `StreamInfo::StreamInfo[in-charge]()'
/home/sammy/musik/libMUSIKEngine.a(mpcdecoder.o)(.text+0x1c4): In function `MUSIKMPCDecoder::~MUSIKMPCDecoder [not-in-charge]()':
/home/sammy/Desktop/wxMusik-0.4.1.0/MUSIKEngine/MUSIKEngine/src/mpcdecoder.cpp:40: undefined reference to `MPC_decoder::~MPC_decoder [in-charge]()'
/home/sammy/musik/libMUSIKEngine.a(mpcdecoder.o)(.text+0x234): In function `MUSIKMPCDecoder::~MUSIKMPCDecoder [in-charge]()':
/home/sammy/Desktop/wxMusik-0.4.1.0/MUSIKEngine/MUSIKEngine/src/mpcdecoder.cpp:40: undefined reference to `MPC_decoder::~MPC_decoder [in-charge]()'
/home/sammy/musik/libMUSIKEngine.a(mpcdecoder.o)(.text+0x2a8): In function `MUSIKMPCDecoder::~MUSIKMPCDecoder [in-charge deleting]()':
/home/sammy/Desktop/wxMusik-0.4.1.0/MUSIKEngine/MUSIKEngine/src/mpcdecoder.cpp:40: undefined reference to `MPC_decoder::~MPC_decoder [in-charge]()'
/home/sammy/musik/libMUSIKEngine.a(mpcdecoder.o)(.text+0x33c): In function `MUSIKMPCDecoder::DoSeek(int)':
/home/sammy/Desktop/wxMusik-0.4.1.0/MUSIKEngine/MUSIKEngine/src/mpcdecoder.cpp:47: undefined reference to `MPC_decoder::SeekSample(long long)'
/home/sammy/musik/libMUSIKEngine.a(mpcdecoder.o)(.text+0x380): In function `MUSIKMPCDecoder::DecodeBlocks(unsigned char*, int)':
/home/sammy/Desktop/wxMusik-0.4.1.0/MUSIKEngine/MUSIKEngine/src/mpcdecoder.cpp:61: undefined reference to `MPC_decoder::Decode(float*, unsigned*, unsigned*)'
/home/sammy/musik/libMUSIKEngine.a(mpcdecoder.o)(.text+0x47a): In function `MUSIKMPCDecoder::OpenMedia(char const*)':
/home/sammy/Desktop/wxMusik-0.4.1.0/MUSIKEngine/MUSIKEngine/src/mpcdecoder.cpp:87: undefined reference to `StreamInfo::ReadStreamInfo(MPC_reader*)'
/home/sammy/musik/libMUSIKEngine.a(mpcdecoder.o)(.text+0x4a1):/home/sammy/Desktop/wxMusik-0.4.1.0/MUSIKEngine/MUSIKEngine/src/mpcdecoder.cpp:93: undefined reference to `MPC_decoder::MPC_decoder[in-charge](MPC_reader*, double)'
/home/sammy/musik/libMUSIKEngine.a(mpcdecoder.o)(.text+0x4b3):/home/sammy/Desktop/wxMusik-0.4.1.0/MUSIKEngine/MUSIKEngine/src/mpcdecoder.cpp:97: undefined reference to `MPC_decoder::Initialize(StreamInfo const*)'
/home/sammy/musik/libMUSIKEngine.a(mpcdecoder.o)(.text+0x4f9):/home/sammy/Desktop/wxMusik-0.4.1.0/MUSIKEngine/MUSIKEngine/src/mpcdecoder.cpp:105: undefined reference to `StreamInfo::GetLengthSamples()'
collect2: ld returned 1 exit status
make[3]: *** [/home/sammy/Desktop/wxMusik-0.4.1.0/crelbuild/wxMusik] Error 1
make[2]: *** [default_target] Error 2
make[1]: *** [default_target_src] Error 2
make: *** [default_target] Error 2
``` 

I think there is an error having to do with "mpcdecoder.o" (but I might be wrong). If that's the case, then I installed the wrong version of libmusepack, which was one of the dependencies. I needed to install libmusepack-1.0.3, but succeeded only in finding libmusepack-1.1.1.., I'm having a devil of a time finding the older version.

Any thoughts??

---

