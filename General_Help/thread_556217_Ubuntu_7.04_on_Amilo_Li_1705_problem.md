---
title: "Ubuntu 7.04 on Amilo Li 1705 problem"
date: 2007-09-21
forum: General Help
---

### Post by blagojedrovski on 2007-09-21
Hi, sorry for my poor English. it's a great honor to be a part of this forum, i have just installed Ubuntu 7.04 and absolutely fell in love with it. Instalation went great, Ubuntu booted and i thought everything went well. 

My problems are theese:

1. My resolution is stuck in 800x600 mode, and somehow can't change it... I've searched in many forums, found drivers on viaarena.com but they can't be installed, since either i'm being a major jackass (because im used to work in windows enviroment) and doing something wrong or i simply can't understand what to do :) I also came across "dpkg-reconfigure xserver-xorg" command (not sure about spelling it right) and after 3 long long hours of changing xorg.config file somehow managed to  fix my resolution but my lame "CN896 VIA Chrome9™" integrated graphics videocard isn't working correctly (works only with the vesa driver)...

2. My sound card which works on my laptop speaker, but when i plug in my headphones it stops, i take my headphones out, it works again (funny huh)... Btw VIA HD Audio Codec VT1708 paired with VT8237A

As i said [http://www.viaarena.com/default.aspx?PageID=2&Type=3&OSID=45]("http://www.viaarena.com/default.aspx?PageID=2&Type=3&OSID=45") has drivers for almoust everything i need but i can't install them. Can someone PLEASE PLEASE PLEASE help me out a bit, this is one hell of an operating system and i intend to learn more and more about it! 

Thank You In Advance!!!

---

### Post by leonidas666 on 2007-09-22
> **blagojedrovski said:**
> 
2. My sound card which works on my laptop speaker, but when i plug in my headphones it stops, i take my headphones out, it works again (funny huh)... Btw VIA HD Audio Codec VT1708 paired with VT8237A

Do you mean to say that there is no sound also on the headphones when you plug in the headphones? Otherwise i think this is a quite usual behavior, when you plug in the headphones the output to the speaker will automatically stop (but of course you should be able to hear something with the headphones)
Otherwise some laptops have lots of different switches for the audio card. You can see these switches if you open the mixer window. One laptop i used had a switch "headphone sense", and this would enable or disable the automatically muting of the speakers when the headphones are inserted. Maybe you can find some setting there.

---

### Post by kecsap on 2007-10-14
I had the same problem and found the solution which works me:

You must patch the hda_codec.c in alsa-driver sources, recompile and install:

[http://forums.viaarena.com/messageview.aspx?catid=28&threadid=77358](http://forums.viaarena.com/messageview.aspx?catid=28&threadid=77358)

That's all

---

### Post by squil on 2007-10-31
I got it to work as well !

the main steps are the following : 

Download the latest alsa driver 

```
tar -xvjf alsa-driver-1.x.xx.tar.bz2
```

open alsa-kernel/pci/hda/patch_via.c

change

```
static int patch_vt1708(struct hda_codec *codec)
{
	struct via_spec *spec;
	int err;

	/* create a codec specific record */
	spec = kcalloc(1, sizeof(*spec), GFP_KERNEL);
	if (spec == NULL)
		return -ENOMEM;

	codec->spec = spec;


	/* automatic parse from the BIOS config */
	err = vt1708_parse_auto_config(codec);
	if (err < 0) {
		via_free(codec);
		return err;
	} else if (!err) {
		printk(KERN_INFO "hda_codec: Cannot set up configuration "
		       "from BIOS.  Using genenic mode...\n");
	}

	
	spec->stream_name_analog = "VT1708 Analog";
	spec->stream_analog_playback = &vt1708_pcm_analog_playback;
	spec->stream_analog_capture = &vt1708_pcm_analog_capture;

	spec->stream_name_digital = "VT1708 Digital";
	spec->stream_digital_playback = &vt1708_pcm_digital_playback;
	spec->stream_digital_capture = &vt1708_pcm_digital_capture;

	
	if (!spec->adc_nids && spec->input_mux) {
		spec->adc_nids = vt1708_adc_nids;
		spec->num_adc_nids = ARRAY_SIZE(vt1708_adc_nids);
		spec->mixers[spec->num_mixers] = vt1708_capture_mixer;
		spec->num_mixers++;
	}

	codec->patch_ops = via_patch_ops;

	codec->patch_ops.init = via_auto_init;
#ifdef CONFIG_SND_HDA_POWER_SAVE
	spec->loopback.amplist = vt1708_loopbacks;
#endif

	return 0;
}
```

by :

 
```
static int patch_vt1708(struct hda_codec *codec)
{
	unsigned int pin_hp; 
	struct via_spec *spec;
	int err;

	/* create a codec specific record */
	spec = kcalloc(1, sizeof(*spec), GFP_KERNEL);
	if (spec == NULL)
		return -ENOMEM;

	codec->spec = spec;

	/* Ajout SQ071031 */
	pin_hp=snd_hda_codec_read(codec, 0x20, 0, AC_VERB_GET_CONFIG_DEFAULT, 0);
	pin_hp=pin_hp&0x3FFFFFFF;
	snd_hda_codec_write(codec, 0x20, 0, AC_VERB_SET_CONFIG_DEFAULT_BYTES_3, pin_hp>>24); 


	/* automatic parse from the BIOS config */
	err = vt1708_parse_auto_config(codec);
	if (err < 0) {
		via_free(codec);
		return err;
	} else if (!err) {
		printk(KERN_INFO "hda_codec: Cannot set up configuration "
		       "from BIOS.  Using genenic mode...\n");
	}

	
	spec->stream_name_analog = "VT1708 Analog";
	spec->stream_analog_playback = &vt1708_pcm_analog_playback;
	spec->stream_analog_capture = &vt1708_pcm_analog_capture;

	spec->stream_name_digital = "VT1708 Digital";
	spec->stream_digital_playback = &vt1708_pcm_digital_playback;
	spec->stream_digital_capture = &vt1708_pcm_digital_capture;

	
	if (!spec->adc_nids && spec->input_mux) {
		spec->adc_nids = vt1708_adc_nids;
		spec->num_adc_nids = ARRAY_SIZE(vt1708_adc_nids);
		spec->mixers[spec->num_mixers] = vt1708_capture_mixer;
		spec->num_mixers++;
	}

	codec->patch_ops = via_patch_ops;

	codec->patch_ops.init = via_auto_init;
#ifdef CONFIG_SND_HDA_POWER_SAVE
	spec->loopback.amplist = vt1708_loopbacks;
#endif

	return 0;
}
```


now, in order to compile : 
```
cd alsa-driver-1.xx.xx
./configure
make
sudo make install
```

Reboot and that should work fine.

---

### Post by blagojedrovski on 2007-11-18
I am so sorry for not responding for such a long time, i've had soo many work this past weeks it was impossible to have some spare time... Anyway THANK YOU a lot, i've done what you told me and it's all working now... Just love the 7.04 version :)

---

### Post by oreja on 2008-02-04
I found the solution which works witch Amilo Pro (Fujitsu Siemens)
You have to add two lines to file /etc/modprobe.d/alsa-base

//add this lines
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto  position_fix=1 enable=yes

and restart laptop. I hope it helps.

---

### Post by shanix on 2008-05-23
Has anyone test the hardware on 8.04 yet??

---

### Post by gnuslov on 2008-05-31
I have an everex gbook va1500v, which has the same sound hardware as the poster that started the thread, and I can report than squil's patch to alsa-drivers works on 8.04, but ONLY if you remove the alsa-driver folder from your /lib/modules/`uname -r`/ubuntu/sound/ directory and replace it with a symbolic link to "../../kernel/sound/" where your new alsa-driver modules are stored.

---

### Post by davidryderuk on 2008-05-31
Thanks,
This works for me in Hardy as well with a Hi-grade computer and via vt1708 audio chip after following squil and gnuslov's instructions. Do you know if this fix going to make it into the unpatched version of alsa at some stage? (it took me about 6 months to find this fix, after i first started with Linux)

---

### Post by swtchrly08 on 2008-06-01
I have followed the guide to install alsa with the changes for this card. I removed the alsa-driver folder from lib modules. But I do not understand where the new alsa driver was installed to create the symbolic link. I installed from my home folder. I'm new so maybe I am missing something really obvious.

---

### Post by gnuslov on 2008-06-03
> **swtchrly08 said:**
> I have followed the guide to install alsa with the changes for this card. I removed the alsa-driver folder from lib modules. But I do not understand where the new alsa driver was installed to create the symbolic link. I installed from my home folder. I'm new so maybe I am missing something really obvious.

When you finished ./configure-ing and making and ran sudo make install in the alsa-driver folder it installed everything into kernel/sound in your kernel's /lib/modules directory.

If you need more help, check out [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/184314") thread from lauchpad where I went into more detail and gave a step by step guide.

---

### Post by olobolger on 2008-07-20
Works just perfectly for me. I've Kubuntu 7.04, kernel 2.6.25.1. All I did is follow the instructions of this thread and the more specific in [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/184314") I've downloaded the alsa-driver 1.0.17, I've made the changes in patch_via.c, then compiled, installed, rebooted, turned up the new Headphone volume slider... and that's all!! :)

   So I don't know why other people have to change symbolic links to folders and things like that (It explained in Launchpad if anyone got problems). Maybe I haven't because is something newly fixed with the 1.0.17 version of alsa-driver or maybe only the users of 8.04 must make this change...

   I'm so happy now, thank you very much :D

---

