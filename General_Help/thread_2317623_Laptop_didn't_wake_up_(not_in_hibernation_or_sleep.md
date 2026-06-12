---
title: "Laptop didn't wake up (not in hibernation or sleep)"
date: 2016-03-18
forum: General Help
---

### Post by allanmills on 2016-03-18
I have a fairly new laptop with Ubuntu 15.10 installed (which I love - I used Kubuntu for years and just switched a couple of months ago).  After work last night, I started my laptop to do a couple of things, and then just left it running when I went to sleep (as I usually do -- and have done before with this laptop with no problems prior to this morning).  I woke up early, found the laptop on as expected, but couldn't stir it to life by moving the mouse or hitting a key on the keyboard as I normally do.  Fan was running, plugged in, all seemed normal except that it was unresponsive.

I didn't know what else to do (later, I thought that maybe I could have gotten into one of the other session terminals, but since the keyboard was unresponsive, I don't know how I would have done this or what I would have done once I got to a terminal), so I just held the power button down until it shut down uncleanly.  Powered it back up and it started up fine, with the attendant "program didn't close properly" messages from Chrome and LibreOffice with offers to restore tabs or documents that had been open (which worked fine).

The system is set up to NOT go into "suspend" or "hibernate" mode ever, so it shouldn't have been in either of those states.

I looked at the system log and tried to copy what I hope are relevant parts from just before I unsuccessfully tried to wake the system up and then when I restarted.  Pasting below -- and if I'm doing this incorrectly, my apologies.  Any ideas on what could have happened from looking at this log portion?  

Thanks for any ideas.

Pasted text below from system log:

Mar 18 02:54:28 Area51 kernel: [11515.532869] perf interrupt took too long (2506 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Mar 18 03:17:01 Area51 CRON[5904]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 18 03:22:58 Area51 gnome-session[2101]: . 2016.03.18 03:22:58 - Updating systems & servers data ...
Mar 18 03:22:59 Area51 gnome-session[2101]: . 2016.03.18 03:22:59 - Systems & servers data update completed
Mar 18 03:43:26 Area51 freshclam[901]: Received signal: wake up
Mar 18 03:43:26 Area51 freshclam[901]: ClamAV update process started at Fri Mar 18 03:43:26 2016
Mar 18 03:43:26 Area51 freshclam[901]: WARNING: Your ClamAV installation is OUTDATED!
Mar 18 03:43:26 Area51 freshclam[901]: WARNING: Local version: 0.98.7 Recommended version: 0.99.1
Mar 18 03:43:26 Area51 freshclam[901]: DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
Mar 18 03:43:26 Area51 freshclam[901]: main.cvd is up to date (version: 57, sigs: 4218790, f-level: 60, builder: amishhammer)
Mar 18 03:43:26 Area51 freshclam[901]: daily.cvd is up to date (version: 21466, sigs: 83889, f-level: 63, builder: amishhammer)
Mar 18 03:43:26 Area51 freshclam[901]: bytecode.cvd is up to date (version: 275, sigs: 45, f-level: 63, builder: amishhammer)
Mar 18 03:52:40 Area51 gnome-session[2101]: I 2016.03.18 03:52:40 - Renewing TLS key
Mar 18 03:52:40 Area51 gnome-session[2101]: . 2016.03.18 03:52:40 - OpenVPN > TLS: tls_process: killed expiring key
Mar 18 03:52:43 Area51 gnome-session[2101]: . 2016.03.18 03:52:43 - OpenVPN > TLS: soft reset sec=0 bytes=74924922/0 pkts=110202/0
Mar 18 03:52:43 Area51 gnome-session[2101]: . 2016.03.18 03:52:43 - OpenVPN > VERIFY OK: depth=1, C=IT, ST=IT, L=Perugia, O=airvpn.org, CN=airvpn.org CA, emailAddress=info@airvpn.org
Mar 18 03:52:43 Area51 gnome-session[2101]: . 2016.03.18 03:52:43 - OpenVPN > Validating certificate key usage
Mar 18 03:52:43 Area51 gnome-session[2101]: . 2016.03.18 03:52:43 - OpenVPN > ++ Certificate has key usage  00a0, expects 00a0
Mar 18 03:52:43 Area51 gnome-session[2101]: . 2016.03.18 03:52:43 - OpenVPN > VERIFY KU OK
Mar 18 03:52:43 Area51 gnome-session[2101]: . 2016.03.18 03:52:43 - OpenVPN > Validating certificate extended key usage
Mar 18 03:52:43 Area51 gnome-session[2101]: . 2016.03.18 03:52:43 - OpenVPN > ++ Certificate has EKU (str) TLS Web Server Authentication, expects TLS Web Server Authentication
Mar 18 03:52:43 Area51 gnome-session[2101]: . 2016.03.18 03:52:43 - OpenVPN > VERIFY EKU OK
Mar 18 03:52:43 Area51 gnome-session[2101]: . 2016.03.18 03:52:43 - OpenVPN > VERIFY OK: depth=0, C=IT, ST=IT, L=Perugia, O=airvpn.org, CN=server, emailAddress=info@airvpn.org
Mar 18 03:52:51 Area51 gnome-session[2101]: . 2016.03.18 03:52:51 - OpenVPN > Data Channel Encrypt: Cipher 'AES-256-CBC' initialized with 256 bit key
Mar 18 03:52:51 Area51 gnome-session[2101]: . 2016.03.18 03:52:51 - OpenVPN > Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mar 18 03:52:51 Area51 gnome-session[2101]: . 2016.03.18 03:52:51 - OpenVPN > Data Channel Decrypt: Cipher 'AES-256-CBC' initialized with 256 bit key
Mar 18 03:52:51 Area51 gnome-session[2101]: . 2016.03.18 03:52:51 - OpenVPN > Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mar 18 03:52:51 Area51 gnome-session[2101]: . 2016.03.18 03:52:51 - OpenVPN > Control Channel: TLSv1.2, cipher TLSv1/SSLv3 DHE-RSA-AES256-GCM-SHA384, 4096 bit RSA
Mar 18 03:53:03 Area51 gnome-session[2101]: . 2016.03.18 03:53:03 - Updating systems & servers data ...
Mar 18 03:53:04 Area51 gnome-session[2101]: . 2016.03.18 03:53:04 - Systems & servers data update completed
Mar 18 04:17:01 Area51 CRON[6363]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 18 04:23:08 Area51 gnome-session[2101]: . 2016.03.18 04:23:08 - Updating systems & servers data ...
Mar 18 04:23:09 Area51 gnome-session[2101]: . 2016.03.18 04:23:09 - Systems & servers data update completed
Mar 18 04:26:58 Area51 kernel: [17061.442474] [drm:atom_op_jump [radeon]] *ERROR* atombios stuck in loop for more than 5secs aborting
Mar 18 04:26:58 Area51 kernel: [17061.442518] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing BE8A (len 114, WS 0, PS 4) @ 0xBEF3
Mar 18 04:26:58 Area51 kernel: [17061.442555] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing E80A (len 2592, WS 0, PS 8) @ 0xEDCE
Mar 18 04:27:04 Area51 kernel: [17066.974702] [drm:atom_op_jump [radeon]] *ERROR* atombios stuck in loop for more than 5secs aborting
Mar 18 04:27:04 Area51 kernel: [17066.974752] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing BE8A (len 114, WS 0, PS 4) @ 0xBEF3
Mar 18 04:27:04 Area51 kernel: [17066.974795] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing E80A (len 2592, WS 0, PS 8) @ 0xE87F
Mar 18 04:27:04 Area51 kernel: [17066.985674] [drm:radeon_dp_link_train [radeon]] *ERROR* clock recovery reached max voltage
Mar 18 04:27:04 Area51 kernel: [17066.985733] [drm:radeon_dp_link_train [radeon]] *ERROR* clock recovery failed
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: snd_pcm_avail() returned a value that is exceptionally large: 934616 bytes (5298 ms).
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: snd_pcm_dump():
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: Soft volume PCM
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: Control: PCM Playback Volume
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: min_dB: -51
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: max_dB: 0
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: resolution: 256
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: Its setup is:
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   stream       : PLAYBACK
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   access       : MMAP_INTERLEAVED
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   format       : S16_LE
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   subformat    : STD
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   channels     : 2
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   rate         : 44100
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   exact rate   : 44100 (44100/1)
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   msbits       : 16
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   buffer_size  : 16384
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   period_size  : 8192
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   period_time  : 185759
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   tstamp_mode  : ENABLE
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   tstamp_type  : MONOTONIC
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   period_step  : 1
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   avail_min    : 15802
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   period_event : 0
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   start_threshold  : -1
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   stop_threshold   : 4611686018427387904
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   silence_threshold: 0
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   silence_size : 0
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   boundary     : 4611686018427387904
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: Slave: Hardware PCM card 1 'HD-Audio Generic' device 0 subdevice 0
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: Its setup is:
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   stream       : PLAYBACK
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   access       : MMAP_INTERLEAVED
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   format       : S16_LE
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   subformat    : STD
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   channels     : 2
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   rate         : 44100
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   exact rate   : 44100 (44100/1)
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   msbits       : 16
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   buffer_size  : 16384
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   period_size  : 8192
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   period_time  : 185759
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   tstamp_mode  : ENABLE
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   tstamp_type  : MONOTONIC
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   period_step  : 1
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   avail_min    : 15802
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   period_event : 0
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   start_threshold  : -1
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   stop_threshold   : 4611686018427387904
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   silence_threshold: 0
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   silence_size : 0
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   boundary     : 4611686018427387904
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   appl_ptr     : 717673601
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   hw_ptr       : 717890871
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: snd_pcm_delay() returned a value that is exceptionally large: -717444 bytes (-4067 ms).
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: snd_pcm_dump():
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: Soft volume PCM
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: Control: PCM Playback Volume
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: min_dB: -51
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: max_dB: 0
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: resolution: 256
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: Its setup is:
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   stream       : PLAYBACK
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   access       : MMAP_INTERLEAVED
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   format       : S16_LE
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   subformat    : STD
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   channels     : 2
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   rate         : 44100
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   exact rate   : 44100 (44100/1)
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   msbits       : 16
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   buffer_size  : 16384
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   period_size  : 8192
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   period_time  : 185759
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   tstamp_mode  : ENABLE
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   tstamp_type  : MONOTONIC
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   period_step  : 1
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   avail_min    : 15802
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   period_event : 0
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   start_threshold  : -1
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   stop_threshold   : 4611686018427387904
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   silence_threshold: 0
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   silence_size : 0
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   boundary     : 4611686018427387904
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: Slave: Hardware PCM card 1 'HD-Audio Generic' device 0 subdevice 0
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c: Its setup is:
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   stream       : PLAYBACK
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   access       : MMAP_INTERLEAVED
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   format       : S16_LE
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   subformat    : STD
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   channels     : 2
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   rate         : 44100
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   exact rate   : 44100 (44100/1)
Mar 18 04:27:04 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   msbits       : 16
Mar 18 04:27:09 Area51 kernel: [17072.043229] [drm:atom_op_jump [radeon]] *ERROR* atombios stuck in loop for more than 5secs aborting
Mar 18 04:27:09 Area51 kernel: [17072.043272] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing BE8A (len 114, WS 0, PS 4) @ 0xBEF3
Mar 18 04:27:09 Area51 kernel: [17072.043308] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing E80A (len 2592, WS 0, PS 8) @ 0xE87F
Mar 18 04:27:09 Area51 kernel: [17072.055702] [drm:radeon_dp_link_train [radeon]] *ERROR* clock recovery reached max voltage
Mar 18 04:27:09 Area51 kernel: [17072.055752] [drm:radeon_dp_link_train [radeon]] *ERROR* clock recovery failed
Mar 18 04:27:09 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   buffer_size  : 16384
Mar 18 04:27:09 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   period_size  : 8192
Mar 18 04:27:09 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   period_time  : 185759
Mar 18 04:27:09 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   tstamp_mode  : ENABLE
Mar 18 04:27:09 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   tstamp_type  : MONOTONIC
Mar 18 04:27:09 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   period_step  : 1
Mar 18 04:27:09 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   avail_min    : 15802
Mar 18 04:27:09 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   period_event : 0
Mar 18 04:27:09 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   start_threshold  : -1
Mar 18 04:27:09 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   stop_threshold   : 4611686018427387904
Mar 18 04:27:09 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   silence_threshold: 0
Mar 18 04:27:09 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   silence_size : 0
Mar 18 04:27:09 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   boundary     : 4611686018427387904
Mar 18 04:27:09 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   appl_ptr     : 717713291
Mar 18 04:27:09 Area51 pulseaudio[2174]: [alsa-sink-ALC3241 Analog] alsa-util.c:   hw_ptr       : 717892652
Mar 18 04:27:14 Area51 kernel: [17077.251690] [drm:atom_op_jump [radeon]] *ERROR* atombios stuck in loop for more than 5secs aborting
Mar 18 04:27:14 Area51 kernel: [17077.251730] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing BE8A (len 114, WS 0, PS 4) @ 0xBEF3
Mar 18 04:27:14 Area51 kernel: [17077.251762] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing E80A (len 2592, WS 0, PS 8) @ 0xEDCE
Mar 18 04:27:19 Area51 kernel: [17082.799868] [drm:atom_op_jump [radeon]] *ERROR* atombios stuck in loop for more than 5secs aborting
Mar 18 04:27:19 Area51 kernel: [17082.799904] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing BE8A (len 114, WS 0, PS 4) @ 0xBEF3
Mar 18 04:27:19 Area51 kernel: [17082.799933] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing E80A (len 2592, WS 0, PS 8) @ 0xEDCE
Mar 18 04:27:26 Area51 kernel: [17088.975657] [drm:atom_op_jump [radeon]] *ERROR* atombios stuck in loop for more than 5secs aborting
Mar 18 04:27:26 Area51 kernel: [17088.975703] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing BE8A (len 114, WS 0, PS 4) @ 0xBEF3
Mar 18 04:27:26 Area51 kernel: [17088.975742] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing E80A (len 2592, WS 0, PS 8) @ 0xEDCE
Mar 18 04:27:31 Area51 kernel: [17094.507905] [drm:atom_op_jump [radeon]] *ERROR* atombios stuck in loop for more than 5secs aborting
Mar 18 04:27:31 Area51 kernel: [17094.507948] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing BE8A (len 114, WS 0, PS 4) @ 0xBEF3
Mar 18 04:27:31 Area51 kernel: [17094.507984] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing E80A (len 2592, WS 0, PS 8) @ 0xE87F
Mar 18 04:27:31 Area51 kernel: [17094.520613] [drm:radeon_dp_link_train [radeon]] *ERROR* clock recovery reached max voltage
Mar 18 04:27:31 Area51 kernel: [17094.520666] [drm:radeon_dp_link_train [radeon]] *ERROR* clock recovery failed
Mar 18 04:27:36 Area51 kernel: [17099.580401] [drm:atom_op_jump [radeon]] *ERROR* atombios stuck in loop for more than 5secs aborting
Mar 18 04:27:36 Area51 kernel: [17099.580446] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing BE8A (len 114, WS 0, PS 4) @ 0xBEF3
Mar 18 04:27:36 Area51 kernel: [17099.580482] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing E80A (len 2592, WS 0, PS 8) @ 0xE87F
Mar 18 04:27:36 Area51 kernel: [17099.597947] [drm:radeon_dp_link_train [radeon]] *ERROR* clock recovery reached max voltage
Mar 18 04:27:36 Area51 kernel: [17099.597995] [drm:radeon_dp_link_train [radeon]] *ERROR* clock recovery failed
Mar 18 04:27:45 Area51 gnome-session[2101]: gnome-session[2101]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Mar 18 04:27:45 Area51 gnome-session[2101]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Mar 18 04:27:45 Area51 gnome-session[2101]: message repeated 2 times: [ GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed]
Mar 18 04:27:45 Area51 gnome-session[2101]: gnome-session[2101]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Mar 18 04:27:45 Area51 gnome-session[2101]: message repeated 2 times: [ gnome-session[2101]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed]
Mar 18 04:27:45 Area51 gnome-session[2101]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Mar 18 04:29:37 Area51 org.freedesktop.Notifications[1994]: ication-rhythmbox' caused error: 'Icon 'notification-rhythmbox' not present in theme ubuntu-mono-dark'loading icon 'notification-rhythmbox' caused error: 'Icon 'notification-rhythmbox' not present in theme ubuntu-mono-dark'loading icon 'notification-rhythmbox' caused error: 'Icon 'notification-rhythmbox' not present in theme ubuntu-mono-dark'loading icon 'notification-rhythmbox' caused error: 'Icon 'notification-rhythmbox' not present in theme ubuntu-mono-dark'loading icon 'notification-rhythmbox' caused error: 'Icon 'notification-rhythmbox' not present in theme ubuntu-mono-dark'loading icon 'notification-rhythmbox' caused error: 'Icon 'notification-rhythmbox' not present in theme ubuntu-mono-dark'loading icon 'notification-rhythmbox' caused error: 'Icon 'notification-rhythmbox' not present in theme ubuntu-mono-dark'loading icon 'notification-rhythmbox' caused error: 'Icon 'notification-rhythmbox' not present in theme ubuntu-mono-dark'loading icon 'notification-rhythmbox' caused error: 'Icon 'notification-rhythmbox' not present in theme ubuntu-mono-dark'loading icon 'notification-rhythmbox' caused error: 'Icon 'notification-rhythmbox' not present in theme ubuntu-mono-dark'loading icon 'notification-rhythmbox' caused error: 'Icon 'notification-rhythmbox' not present in theme ubuntu-mono-dark'loading icon 'notification-rhythmbox' caused error: 'Icon 'notification-rhythmbox' not present in theme ubuntu-mono-dark'loading icon 'notification-rhythmbox' caused error: 'Icon 'notification-rhythmbox' not present in theme ubuntu-mono-dark'loading icon 'notification-rhythmbox' caused error: 'Icon 'notification-rhythmbox' not present in theme ubuntu-mono-dark'loading icon 'notification-rhythmbox' caused error: 'Icon 'notification-rhythmbox' not present in theme ubuntu-mono-dark'loading icon 'notification-rhythmbox' caused error: 'Icon 'notification-rhythmbox' not present in theme ubuntu-mono-dark'loading icon 'notification-rhythmbox' caused error: 'Icon 'notification-rhythmbox' not present in theme ubuntu-mono-dark'loading ic
Mar 18 04:31:26 Area51 kernel: [17328.704005] atkbd serio0: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
Mar 18 04:31:26 Area51 kernel: [17328.704016] atkbd serio0: Use 'setkeycodes e058 <keycode>' to make it known.
Mar 18 04:31:26 Area51 kernel: [17328.767514] atkbd serio0: Unknown key released (translated set 2, code 0xd8 on isa0060/serio0).
Mar 18 04:31:26 Area51 kernel: [17328.767525] atkbd serio0: Use 'setkeycodes e058 <keycode>' to make it known.
Mar 18 04:31:26 Area51 NetworkManager[920]: <info>  sleep requested (sleeping: no  enabled: yes)
Mar 18 04:31:26 Area51 NetworkManager[920]: <info>  sleeping...
Mar 18 04:31:26 Area51 NetworkManager[920]: <info>  (wlo1): device state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
Mar 18 04:31:26 Area51 NetworkManager[920]: <info>  (wlo1): canceled DHCP transaction, DHCP client pid 1080
Mar 18 04:31:26 Area51 NetworkManager[920]: <info>  (wlo1): DHCPv4 state changed bound -> done
Mar 18 04:31:26 Area51 avahi-daemon[902]: Withdrawing address record for 192.168.1.4 on wlo1.
Mar 18 04:31:26 Area51 avahi-daemon[902]: Leaving mDNS multicast group on interface wlo1.IPv4 with address 192.168.1.4.
Mar 18 04:31:26 Area51 avahi-daemon[902]: Interface wlo1.IPv4 no longer relevant for mDNS.
Mar 18 04:31:26 Area51 avahi-daemon[902]: Withdrawing address record for fe80::1a4f:32ff:fe9d:6432 on wlo1.
Mar 18 04:31:26 Area51 avahi-daemon[902]: Leaving mDNS multicast group on interface wlo1.IPv6 with address fe80::1a4f:32ff:fe9d:6432.
Mar 18 04:31:26 Area51 avahi-daemon[902]: Interface wlo1.IPv6 no longer relevant for mDNS.
Mar 18 04:31:26 Area51 kernel: [17329.158825] wlo1: deauthenticating from c0:3f:0e:ef:ba:a6 by local choice (Reason: 3=DEAUTH_LEAVING)
Mar 18 04:31:26 Area51 dnsmasq[1115]: setting upstream servers from DBus
Mar 18 04:31:26 Area51 wpa_supplicant[998]: wlo1: CTRL-EVENT-DISCONNECTED bssid=c0:3f:0e:ef:ba:a6 reason=3 locally_generated=1
Mar 18 04:31:26 Area51 NetworkManager[920]: <info>  Writing DNS information to /sbin/resolvconf
Mar 18 04:31:26 Area51 NetworkManager[920]: <info>  NetworkManager state is now ASLEEP
Mar 18 04:31:26 Area51 dbus[924]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Mar 18 04:31:27 Area51 NetworkManager[920]: <warn>  Failed to GDBus.Error:fi.w1.wpa_supplicant1.NotConnected: This interface is not connected: disconnect.
Mar 18 04:31:27 Area51 wpa_supplicant[998]: nl80211: deinit ifname=wlo1 disabled_11b_rates=0
Mar 18 04:31:32 Area51 kernel: [17334.737831] [drm:atom_op_jump [radeon]] *ERROR* atombios stuck in loop for more than 5secs aborting
Mar 18 04:31:32 Area51 kernel: [17334.737871] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing BE8A (len 114, WS 0, PS 4) @ 0xBEF3
Mar 18 04:31:32 Area51 kernel: [17334.737901] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing E80A (len 2592, WS 0, PS 8) @ 0xEDCE
Mar 18 04:31:33 Area51 kernel: [17335.688126] atkbd serio0: Unknown key pressed (translated set 2, code 0xd7 on isa0060/serio0).
Mar 18 04:31:33 Area51 kernel: [17335.688134] atkbd serio0: Use 'setkeycodes e057 <keycode>' to make it known.
Mar 18 04:31:33 Area51 kernel: [17335.721095] atkbd serio0: Unknown key released (translated set 2, code 0xd7 on isa0060/serio0).
Mar 18 04:31:33 Area51 kernel: [17335.721102] atkbd serio0: Use 'setkeycodes e057 <keycode>' to make it known.
Mar 18 04:31:37 Area51 kernel: [17340.309936] [drm:atom_op_jump [radeon]] *ERROR* atombios stuck in loop for more than 5secs aborting
Mar 18 04:31:37 Area51 kernel: [17340.309974] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing BE8A (len 114, WS 0, PS 4) @ 0xBEF3
Mar 18 04:31:37 Area51 kernel: [17340.310006] [drm:atom_execute_table_locked [radeon]] *ERROR* atombios stuck executing E80A (len 2592, WS 0, PS 8) @ 0xEDCE
Mar 18 04:31:38 Area51 kernel: [17340.661900] cfg80211: World regulatory domain updated:
Mar 18 04:31:38 Area51 kernel: [17340.661908] cfg80211:  DFS Master region: unset
Mar 18 04:31:38 Area51 kernel: [17340.661911] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Mar 18 04:31:38 Area51 kernel: [17340.661917] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Mar 18 04:31:38 Area51 kernel: [17340.661921] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Mar 18 04:31:38 Area51 kernel: [17340.661924] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Mar 18 04:31:38 Area51 kernel: [17340.661928] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Mar 18 04:31:38 Area51 kernel: [17340.661932] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Mar 18 04:31:38 Area51 kernel: [17340.661936] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Mar 18 04:31:38 Area51 kernel: [17340.661939] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Mar 18 04:31:38 Area51 kernel: [17340.661942] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Mar 18 04:31:38 Area51 systemd-udevd[6475]: Process '/sbin/crda' failed with exit code 249.
Mar 18 04:31:38 Area51 systemd-udevd[6475]: message repeated 2 times: [ Process '/sbin/crda' failed with exit code 249.]
Mar 18 04:31:38 Area51 systemd[1]: Reached target Sleep.
Mar 18 04:31:38 Area51 systemd[1]: Starting Suspend...
Mar 18 04:31:38 Area51 systemd[1]: Starting Network Manager Script Dispatcher Service...
Mar 18 04:31:38 Area51 systemd-sleep[6496]: Suspending system...

Mar 18 08:34:07 Area51 systemd-modules-load[281]: Inserted module 'dm_crypt'
Mar 18 08:34:07 Area51 systemd-modules-load[281]: Module 'loop' is builtin
Mar 18 08:34:07 Area51 systemd-modules-load[281]: Inserted module 'lp'
Mar 18 08:34:07 Area51 systemd-modules-load[281]: Inserted module 'ppdev'
Mar 18 08:34:07 Area51 systemd-modules-load[281]: Inserted module 'parport_pc'
Mar 18 08:34:07 Area51 systemd[1]: Started Load Kernel Modules.
Mar 18 08:34:07 Area51 systemd[1]: Starting Apply Kernel Variables...
Mar 18 08:34:07 Area51 systemd[1]: Mounting FUSE Control File System...
Mar 18 08:34:07 Area51 systemd[1]: Mounted FUSE Control File System.
Mar 18 08:34:07 Area51 systemd[1]: Started Create Static Device Nodes in /dev.
Mar 18 08:34:07 Area51 systemd[1]: Starting udev Kernel Device Manager...
Mar 18 08:34:07 Area51 systemd[1]: Started Apply Kernel Variables.
Mar 18 08:34:07 Area51 systemd-udevd[310]: unknown key 'SYSFS{idVendor}' in /etc/udev/rules.d/40-brother-libsane-type1.rules:17
Mar 18 08:34:07 Area51 systemd-udevd[310]: invalid rule '/etc/udev/rules.d/40-brother-libsane-type1.rules:17'
Mar 18 08:34:07 Area51 systemd[1]: Started udev Kernel Device Manager.
Mar 18 08:34:07 Area51 systemd[1]: Starting Remount Root and Kernel File Systems...
Mar 18 08:34:07 Area51 systemd[1]: Starting Show Plymouth Boot Screen...
Mar 18 08:34:07 Area51 systemd[1]: Started Remount Root and Kernel File Systems.
Mar 18 08:34:07 Area51 systemd[1]: Starting Load/Save Random Seed...
Mar 18 08:34:07 Area51 systemd[1]: Starting Flush Journal to Persistent Storage...
Mar 18 08:34:07 Area51 systemd[1]: Reached target Local File Systems (Pre).
Mar 18 08:34:07 Area51 systemd[1]: Started Flush Journal to Persistent Storage.
Mar 18 08:34:07 Area51 systemd[1]: Started Load/Save Random Seed.
Mar 18 08:34:07 Area51 systemd[1]: Started Show Plymouth Boot Screen.
Mar 18 08:34:07 Area51 systemd[1]: Started Forward Password Requests to Plymouth Directory Watch.
Mar 18 08:34:07 Area51 systemd[1]: Created slice system-systemd\x2dbacklight.slice.
Mar 18 08:34:07 Area51 systemd[1]: Starting Load/Save Screen Backlight Brightness of backlight:radeon_bl0...
Mar 18 08:34:07 Area51 systemd[1]: Started Load/Save Screen Backlight Brightness of backlight:radeon_bl0.






****************************************************************************************************************



Mar 18 08:34:32 Area51 gnome-session[1979]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Mar 18 08:34:32 Area51 gnome-session[1979]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Mar 18 08:34:32 Area51 dbus[929]: [system] Activating via systemd: service name='org.freedesktop.locale1' unit='dbus-org.freedesktop.locale1.service'
Mar 18 08:34:32 Area51 gnome-session[1979]: SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Mar 18 08:34:32 Area51 systemd[1]: Starting Locale Service...
Mar 18 08:34:32 Area51 dbus[929]: [system] Successfully activated service 'org.freedesktop.locale1'
Mar 18 08:34:32 Area51 systemd[1]: Started Locale Service.
Mar 18 08:34:34 Area51 gnome-session[1979]: (gsettings-data-convert:2050): GLib-GIO-ERROR **: Settings schema 'org.gnome.totem' does not contain a key named 'debug'
Mar 18 08:34:34 Area51 kernel: [   52.879477] do_trap: 45 callbacks suppressed
Mar 18 08:34:34 Area51 kernel: [   52.879486] traps: gsettings-data-[2050] trap int3 ip:7f9dfb98289b sp:7ffdea6b16a0 error:0
Mar 18 08:34:35 Area51 gnome-session[1979]: gnome-session[1979]: WARNING: Application 'gsettings-data-convert.desktop' killed by signal 5
Mar 18 08:34:35 Area51 gnome-session[1979]: WARNING: Application 'gsettings-data-convert.desktop' killed by signal 5
Mar 18 08:34:35 Area51 gnome-session[1979]: (gsettings-data-convert:2140): GLib-GIO-ERROR **: Settings schema 'org.gnome.totem' does not contain a key named 'debug'
Mar 18 08:34:35 Area51 kernel: [   53.778735] traps: gsettings-data-[2140] trap int3 ip:7f64dbb3289b sp:7ffcb1258d00 error:0
Mar 18 08:34:35 Area51 gnome-session[1979]: gnome-session[1979]: WARNING: Application 'gsettings-data-convert.desktop' killed by signal 5
Mar 18 08:34:35 Area51 gnome-session[1979]: gnome-session[1979]: WARNING: App 'gsettings-data-convert.desktop' respawning too quickly
Mar 18 08:34:35 Area51 gnome-session[1979]: WARNING: Application 'gsettings-data-convert.desktop' killed by signal 5
Mar 18 08:34:35 Area51 gnome-session[1979]: WARNING: App 'gsettings-data-convert.desktop' respawning too quickly
Mar 18 08:34:35 Area51 gnome-session[1979]: WARNING: Error on restarting session managed app: Component 'gsettings-data-convert.desktop' crashing too quickly
Mar 18 08:34:35 Area51 gnome-session[1979]: gnome-session[1979]: WARNING: Error on restarting session managed app: Component 'gsettings-data-convert.desktop' crashing too quickly
Mar 18 08:34:36 Area51 gnome-session[1979]: (process:2167): indicator-application-service-WARNING **: Unable to get watcher name 'org.kde.StatusNotifierWatcher'
Mar 18 08:34:36 Area51 gnome-session[1979]: (process:2167): indicator-application-service-WARNING **: Name Lost
Mar 18 08:34:36 Area51 gnome-session[1979]: Entering running state
Mar 18 08:34:36 Area51 dbus[929]: [system] Activating via systemd: service name='org.freedesktop.UDisks2' unit='udisks2.service'
Mar 18 04:34:18 Area51 systemd[1723]: Time has been changed
Mar 18 04:34:18 Area51 systemd-timesyncd[809]: Synchronized to time server 91.189.89.199:123 (ntp.ubuntu.com).
Mar 18 04:34:18 Area51 systemd[1349]: Time has been changed
Mar 18 04:34:18 Area51 systemd[1]: Time has been changed
Mar 18 04:34:18 Area51 systemd[1]: Starting Disk Manager...
Mar 18 04:34:18 Area51 udisksd[2191]: udisks daemon version 2.1.6 starting
Mar 18 04:34:18 Area51 dbus[929]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Mar 18 04:34:18 Area51 systemd[1]: Started Disk Manager.

---

