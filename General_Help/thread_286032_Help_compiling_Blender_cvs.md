---
title: "Help compiling Blender cvs"
date: 2006-10-27
forum: General Help
---

### Post by Nano Geek on 2006-10-27
I am having problems compiling Blender from cvs on my "Edgy" computer. I have  tried using scons and here's what I get:```
scons: Reading SConscript files ...
Command-line arguments
        BF_TOOLSET = mingw
        BF_BUILDDIR = c:buildinstall
Command-line targets
        No targets given, using default
Using mingw
Using config file: config/linux2-config.py
Using config file: user-config.py
Linux platform detected:
  checking for FreeAlut... (cached) no
Building in c:buildinstall/
Configuring library bf_soundsystem
Configuring library bf_string
Configuring library bf_ghost
Configuring library bf_guardedalloc
Configuring library bf_bmfont
Configuring library bf_moto
Configuring library blender_CTR
Configuring library bf_memutil
Configuring library bf_decimation
Configuring library blender_IK
Configuring library blender_bop
Configuring library blender_ONL
Configuring library bf_elbeem
Configuring library blender_BSP
Configuring library extern_qhull
Configuring library extern_solid
Configuring library extern_bullet
Configuring library extern_ftgl
Configuring library bf_avi
Configuring library bf_blenkernel
Configuring library bf_blenlib
Configuring library bf_blenloader
Configuring library bf_blenpluginapi
Configuring library bf_imbuf
Configuring library bf_cineon
Configuring library blender_img
Configuring library bf_dna
Configuring library blender_python
Configuring library blender_radiosity
Configuring library bf_readblenfile
Configuring library blender_render
Configuring library src
Configuring library bf_yafray
Configuring library bf_ftfont
Configuring library bf_openexr
Configuring library bf_kernel
Configuring library blender_creator
Configuring library bf_bloutines
Configuring library bf_converter
Configuring library bf_expressions
Configuring library bf_logic
Configuring library bf_ketsji
Configuring library kx_network
Configuring library bf_ngnetwork
Configuring library bf_loopbacknetwork
Configuring library bf_common
Configuring library bf_dummy
Configuring library bf_rasterizer
Configuring library bf_oglrasterizer
Configuring library bf_scenegraph
Configuring library bf_bullet
Configuring library bf_sumo
Configuring program blender
scons: done reading SConscript files.
scons: Building targets ...
Compiling ==> 'SND_OpenALDevice.cpp'
intern/SoundSystem/openal/SND_OpenALDevice.cpp:46:19: error: AL/al.h: No such file or directory
intern/SoundSystem/openal/SND_OpenALDevice.cpp:47:20: error: AL/alc.h: No such file or directory
intern/SoundSystem/openal/SND_OpenALDevice.cpp:48:21: error: AL/alut.h: No such file or directory
intern/SoundSystem/openal/SND_OpenALDevice.cpp:66: error: ‘ALvoid’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:67: error: ‘ALvoid’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:71: error: ‘ALubyte’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:72: error: ‘ALsizei’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:73: error: ‘ALubyte’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:78: error: ‘ALushort’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:79: error: ‘ALushort’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:80: error: ‘ALuint’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:81: error: ‘ALuint’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:82: error: ‘ALushort’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:83: error: ‘ALushort’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:88: error: ‘ALushort’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:89: error: ‘ALushort’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:94: error: ‘ALuint’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:95: error: ‘ALuint’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:96: error: ‘ALuint’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:97: error: ‘ALuint’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:98: error: ‘ALuint’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:99: error: ‘ALuint’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:100: error: ‘ALuint’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:101: error: ‘ALuint’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:102: error: ‘ALuint’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:105: error: ‘ALuint’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:106: error: ‘ALuint’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:107: error: ‘ALuint’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:108: error: ‘ALuint’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:109: error: ‘ALuint’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:110: error: ‘ALuint’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:116: error: ‘ALubyte’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:117: error: ‘ALuint’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:120: error: ‘ALvoid’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp:195: error: ‘ALvoid’ does not name a type
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In constructor ‘SND_OpenALDevice::SND_OpenALDevice()’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:229: error: ‘ALCdevice’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:229: error: ‘dev’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:229: error: ‘alcOpenDevice’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:231: error: ‘alcCreateContext’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:237: error: ‘alcMakeContextCurrent’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:265: error: ‘alGenBuffers’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:270: error: ‘alIsBuffer’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:288: error: ‘ALenum’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:288: error: expected `;' before ‘alc_error’
intern/SoundSystem/openal/SND_OpenALDevice.cpp:292: error: ‘alc_error’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:292: error: ‘ALC_NO_ERROR’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:294: error: ‘alGenSources’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In destructor ‘virtual SND_OpenALDevice::~SND_OpenALDevice()’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:331: error: ‘alDeleteBuffers’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:338: error: ‘alSourceStop’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:340: error: ‘alDeleteSources’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:349: error: ‘alcDestroyContext’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:375: error: ‘ALCdevice’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:375: error: expected primary-expression before ‘)’ token
intern/SoundSystem/openal/SND_OpenALDevice.cpp:375: error: ‘alcCloseDevice’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual SND_WaveSlot* SND_OpenALDevice::LoadSample(const STR_String&, void*, int)’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:404: error: ‘ALenum’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:404: error: expected `;' before ‘al_error’
intern/SoundSystem/openal/SND_OpenALDevice.cpp:435: error: ‘alutLoadWAVMemory’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:440: error: ‘alBufferData’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:448: error: ‘ALbyte’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:448: error: expected primary-expression before ‘)’ token
intern/SoundSystem/openal/SND_OpenALDevice.cpp:448: error: ‘alutLoadWAVFile’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:451: error: ‘alBufferData’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:455: error: ‘al_error’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:455: error: ‘alGetError’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:456: error: ‘AL_NO_ERROR’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:476: error: ‘alutUnloadWAV’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual void SND_OpenALDevice::SetDopplerVelocity(MT_Scalar) const’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:498: error: ‘alDopplerVelocity’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual void SND_OpenALDevice::SetDopplerFactor(MT_Scalar) const’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:506: error: ‘alDopplerFactor’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual void SND_OpenALDevice::SetListenerGain(float) const’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:533: error: ‘AL_GAIN’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:533: error: ‘alListenerf’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual void SND_OpenALDevice::InitListener()’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:552: error: ‘AL_POSITION’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:552: error: ‘alListenerfv’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:553: error: ‘AL_VELOCITY’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:554: error: ‘AL_ORIENTATION’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual void SND_OpenALDevice::SetObjectBuffer(int, unsigned int)’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:566: error: ‘AL_BUFFER’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:566: error: ‘alSourcei’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual int SND_OpenALDevice::GetPlayState(int)’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:580: error: ‘AL_SOURCE_STATE’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:580: error: ‘alGetSourceiv’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:585: error: ‘AL_INITIAL’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:590: error: ‘AL_PLAYING’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:595: error: ‘AL_PAUSED’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:600: error: ‘AL_STOPPED’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual void SND_OpenALDevice::PlayObject(int)’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:617: error: ‘alSourcePlay’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual void SND_OpenALDevice::StopObject(int) const’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:628: error: ‘AL_POSITION’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:628: error: ‘alSourcefv’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:629: error: ‘AL_VELOCITY’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:631: error: ‘AL_GAIN’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:631: error: ‘alSourcef’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:632: error: ‘AL_PITCH’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:633: error: ‘AL_FALSE’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:633: error: ‘alSourcei’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:634: error: ‘alSourceStop’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual void SND_OpenALDevice::StopAllObjects()’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:642: error: ‘alSourceStopv’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual void SND_OpenALDevice::PauseObject(int) const’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:650: error: ‘alSourcePause’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual void SND_OpenALDevice::SetObjectPitch(int, MT_Scalar) const’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:662: error: ‘AL_PITCH’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:662: error: ‘alSourcef’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual void SND_OpenALDevice::SetObjectGain(int, MT_Scalar) const’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:670: error: ‘AL_GAIN’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:670: error: ‘alSourcef’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual void SND_OpenALDevice::SetObjectLoop(int, unsigned int) const’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:681: error: ‘AL_FALSE’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:681: error: ‘alSourcei’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:684: error: ‘AL_TRUE’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:684: error: ‘alSourcei’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual void SND_OpenALDevice::SetObjectMinGain(int, MT_Scalar) const’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:696: error: ‘AL_MIN_GAIN’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:696: error: ‘alSourcef’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual void SND_OpenALDevice::SetObjectMaxGain(int, MT_Scalar) const’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:703: error: ‘AL_MAX_GAIN’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:703: error: ‘alSourcef’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual void SND_OpenALDevice::SetObjectRollOffFactor(int, MT_Scalar) const’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:710: error: ‘AL_ROLLOFF_FACTOR’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:710: error: ‘alSourcef’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual void SND_OpenALDevice::SetObjectReferenceDistance(int, MT_Scalar) const’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:717: error: ‘AL_REFERENCE_DISTANCE’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:717: error: ‘alSourcef’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual void SND_OpenALDevice::ObjectIs2D(int) const’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:728: error: ‘AL_POSITION’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:728: error: ‘alSourcefv’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:729: error: ‘AL_VELOCITY’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp: In member function ‘virtual void SND_OpenALDevice::SetObjectTransform(int, const MT_Vector3&, const MT_Vector3&, const MT_Matrix3x3&, const MT_Vector3&, const MT_Scalar&) const’:
intern/SoundSystem/openal/SND_OpenALDevice.cpp:748: error: ‘AL_POSITION’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:748: error: ‘alSourcefv’ was not declared in this scope
intern/SoundSystem/openal/SND_OpenALDevice.cpp:751: error: ‘AL_VELOCITY’ was not declared in this scope
scons: *** [c:buildinstall/intern/SoundSystem/openal/SND_OpenALDevice.o] Error 1
scons: building terminated because of errors.

```I any one knows how to do this properly, please help me.
Thanks

---

### Post by Nano Geek on 2006-10-27
Anyone?

---

