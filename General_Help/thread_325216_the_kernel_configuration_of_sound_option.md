---
title: "the kernel configuration of sound option"
date: 2006-12-25
forum: General Help
---

### Post by LaoLiulaoliu on 2006-12-25
My cpu is AMD Opteron/Athlon64/FX.my motherboard's chip set is nvidia GeForce6100(C61) I only have one sound card ,that is on my motherboard,Realtek ALC888 7.1 sound track CODEC,Premium level&#65288;High DefinitionAudio&#65289;.The new kernel is 2.6.19.1.
This is my configuration about the sound.please tell me where is wrong.
[]Open Sound System (DEPRECATED)
[M]Advanced Linux Sound Architecture
	[M]Sequencer support
		[]Sequencer dummy client 
	[M]OSS Mixer API
	[M]OSS PCM (digital audio) API
		[*]OSS PCM (digital audio) API - Include plugin system 
	[]OSS Sequencer API
	[M]RTC Timer support
		[*]Use RTC as default sequencer timer
	[*]Dynamic device file minor numbers
	[*]Support old ALSA API
	[*]Verbose procfs contents
	[]Verbose printk
	[]Debug

Generic devices -->
	//choose nothing
PCI devices -->
	[]Analog Devices AD1889
	[]Avance Logic ALS300/ALS300+
	[]Avance Logic ALS4000 
	[]ALi M5451 PCI Audio Controller
	[]ATI IXP AC97 Controller
	[]ATI IXP Modem 
	[]Aureal Advantage 
	[]Aureal Vortex
	[]Aureal Vortex 2 
	[]Aztech AZF3328 / PCI168 (EXPERIMENTAL)
	[]Bt87x Audio Capture
	[]SB Audigy LS / Live 24bit
	[]C-Media 8738, 8338
	[]Cirrus Logic (Sound Fusion) CS4281
	[]Cirrus Logic (Sound Fusion) CS4280/CS461x/CS462x/CS463x 
	[M](Echoaudio) Darla20
	[M](Echoaudio) Gina20 
	[M](Echoaudio) Layla20 
	[M](Echoaudio) Darla24
	[M](Echoaudio) Gina24
	[M](Echoaudio) Layla24
	[M](Echoaudio) Mona 
	[M](Echoaudio) Mia
	[M](Echoaudio) 3G cards 
	[M](Echoaudio) Indigo
	[M](Echoaudio) Indigo IO
	[M](Echoaudio) Indigo DJ
	[]Emu10k1 (SB Live!, Audigy, E-mu APS)
	[]Emu10k1X (Dell OEM Version)
	[](Creative) Ensoniq AudioPCI 1370
	[](Creative) Ensoniq AudioPCI 1371/1373
	[]ESS ES1938/1946/1969 (Solo-1)
	[]ESS ES1968/1978 (Maestro-1/2/2E)
	[]ForteMedia FM801
	[M]Intel HD Audio	
	[]RME Hammerfall DSP Audio
	[]RME Hammerfall DSP MADI
	[]ICEnsemble ICE1712 (Envy24)
	[]ICE/VT1724/1720 (Envy24HT/PT) 
	[]Intel/SiS/nVidia/AMD/ALi AC97 Controller
	[]Intel/SiS/nVidia/AMD MC97 Modem
	[]Korg 1212 IO
	[]ESS Allegro/Maestro3
	[]Digigram miXart 
	[]NeoMagic NM256AV/ZX
	[]Digigram PCXHR
	[]Conexant Riptide
	[]RME Digi32, 32/8, 32 PRO 
	[]RME Digi96, 96/8, 96/8 PRO
	[]RME Digi9652 (Hammerfall)
	[]S3 SonicVibes
	[]Trident 4D-Wave DX/NX; SiS 7018
	[]VIA 82C686A/B, 8233/8235 AC97 Controller
	[]VIA 82C686A/B, 8233 based Modems
	[]Digigram VX222 
	[]Yamaha YMF724/740/744/754
	[*]AC97 Power-Saving Mode
USB devices -->
	//choose nothing

---

