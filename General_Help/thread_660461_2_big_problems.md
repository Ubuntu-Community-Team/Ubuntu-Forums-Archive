---
title: "2 big problems"
date: 2008-01-06
forum: General Help
---

### Post by katsou on 2008-01-06
Before a few days i've decided to install ubuntu on my 3rd pc but i've never have thought what will follow.

1st prob
when i try to watch tv.No sound from my speakers.I play with the audio settings and everything around that have common with sound but nothing.I disconnect my speakers from sound card and i connect them direct to tv tuner and suddenly sound decided to play.

dmesg

```

[   32.341816] bttv: driver version 0.9.17 loaded
[   32.341823] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   32.341903] bttv: Bt8xx card found (0).
[   32.341939] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 18
[   32.341953] bttv0: Bt878 (rev 17) at 0000:00:0b.0, irq: 18, latency: 32, mmio: 0xef000000
[   32.341968] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   32.341972] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   32.342017] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[   32.344505] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   32.370743] tveeprom 1-0050: Hauppauge model 44804, rev C108, serial# 2361824
[   32.370748] tveeprom 1-0050: tuner model is Philips FI1216 MK2 (idx 8, type 5)
[   32.370752] tveeprom 1-0050: TV standards PAL(B/G) (eeprom 0x04)
[   32.370755] tveeprom 1-0050: audio processor is None (idx 0)
[   32.370758] tveeprom 1-0050: has no radio
[   32.370760] bttv0: Hauppauge eeprom indicates model#44804
[   32.370764] bttv0: using tuner=5
[   32.370769] bttv0: i2c: checking for MSP34xx @ 0x80... <4>nvidia: module license 'NVIDIA' taints kernel.
[   32.543113] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[   32.872156] input: PC Speaker as /class/input/input3
[   32.899104] parport_pc 00:09: reported by Plug and Play ACPI
[   32.899171] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   33.088808] not found
[   33.088817] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   33.177568] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   33.407999] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   33.433135] tuner 1-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   33.433188] tuner 1-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   33.433193] tuner 1-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   33.440285] bttv0: registered device video0
[   33.440329] bttv0: registered device vbi0
[   33.440351] bttv0: PLL: 28636363 => 35468950 .. ok
[   33.470190] ACPI: PCI Interrupt 0000:00:0b.1[A] -> GSI 19 (level, low) -> IRQ 18
[   33.481533] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 19
[   33.482147] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   33.486407] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 17 (level, low) -> IRQ 20
[   33.488715] Audigy2 value: Special config.
[   33.585964] bt878: AUDIO driver version 0.0.0 loaded


```


lsmod


```

snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         8064  1 snd_emux_synth
bt878                  11832  0 
snd_seq_midi_emul       7680  1 snd_emux_synth
tuner                  63144  0 
tvaudio                24348  0 
snd_emu10k1           137248  2 snd_emu10k1_synth
snd_ac97_codec        100644  1 snd_emu10k1
ac97_bus                3200  1 snd_ac97_codec
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10244  2 snd_emux_synth,snd_emu10k1
analog                 13344  0 
snd_seq_dummy           4740  0 
gameport               16776  1 analog
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
nvidia               4716468  32 
snd_bt87x              16420  0 
bttv                  177012  1 bt878
video_buf              26244  1 bttv
ir_common              35460  1 bttv
i2c_viapro             10004  0 
snd_rawmidi            25728  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
compat_ioctl32          2304  1 bttv
i2c_algo_bit            7428  1 bttv
btcx_risc               5896  1 bttv
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
via_ircc               27668  0 
irda                  202300  1 via_ircc
tveeprom               16784  1 bttv
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
i2c_core               26112  7 tuner,tvaudio,nvidia,bttv,i2c_viapro,i2c_algo_bit,tveeprom
snd_pcm                80388  4 snd_emu10k1,snd_ac97_codec,snd_bt87x,snd_pcm_oss
snd_page_alloc         11400  3 snd_emu10k1,snd_bt87x,snd_pcm
crc_ccitt               3072  1 irda
serio_raw               8068  0 
psmouse                39952  0 
snd_seq                53232  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9228  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  16 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_hwdep,snd_seq_oss,snd_bt87x,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
via_agp                11264  1 
agpgart                35016  2 nvidia,via_agp
videodev               29312  1 bttv
v4l2_common            18432  4 tuner,tvaudio,bttv,videodev
v4l1_compat            15364  2 bttv,videodev


```

lspci

```

00:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
00:0e.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value


```

2nd problem

i decided to install firestarter.I did succesfully but when i try to launch it,it gives me this

```

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:8549): Gtk-WARNING **: cannot open display:  


```

Can anybody help me?

---

### Post by AlexThomson_NZ on 2008-01-06
These problems are probably related.  Are you trying to do anything tricky like run these over SSH by any chance?  (I do a similar thing at some with my laptop connected to my home theatre)

The error "Xlib: connection to ":0.0" refused by server" is a clue- do you actually have X running on :0?

---

### Post by strabes on 2008-01-06
Just for your information, you only need to install firestarter if you specifically want to open ports in ubuntu. They're all closed by default.

---

### Post by Easy_Rider9999 on 2008-05-23
Connect the sound outlet of your TV-card with line-input and turn on line-input in the alsa mixer.

---

