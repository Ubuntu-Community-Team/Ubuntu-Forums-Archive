---
title: "Cannot connect Openswan to Sonicwall"
date: 2006-07-12
forum: General Help
---

### Post by 1T-M0nk3y on 2006-07-12
UPDATE:
I have now had a chance to get into work in time to catch the logs on the firewall, which read:
RECEIVED<<< ISAKMP OAK AG (InitCookie 0xa1b340472acb64ac, MsgID: 0x0) (SA, KE, NON, ID, VID, VID, VID, VID, VID, VID) openswan.ip, 500 sonicwall.ip, 500
IKE Responder: Received Aggressive Mode request (Phase 1) openswan.ip, 500 sonicwall.ip, 62465
SENDING>>>> ISAKMP OAK AG (InitCookie 0xa1b340472acb64ac, MsgID: 0x0) (SA, KE, VID, NATD, NATD, NON, ID, VID, VID, HASH) sonicwall.ip, 500 openswan.ip, 500
Header verification failed openswan.ip, 500 sonicwall.ip, 500
IKE Responder: No response - remote party timeout sonicwall.ip, 500 openswan.ip, 500
Received packet retransmission. Drop duplicate packet openswan.ip, 500 sonicwall.ip, 500
[These last two appear three times each]
IKE negotiation aborted due to timeout sonicwall.ip openswan.ip

That's it, it sounds as though the sonicwall is sending the messages back to openswan but they are never received, or at least openswan doesn't do anything with them, it doesn't even log that it has received the packets, even though there is currently no firewall running when I test!  Confused :confused: 

ORIGINAL MESSAGE:
Apparently it's possible, but I have yet to get it working, it seems to send the request but never receives a reply, I've check that the firewall isn't blocking it, I've checked that pluto is running and I've checked that the settings in the sonicwall and in ipsec.conf match that in the instructions from sonicwall, but whether I try sudo ipsec auto --up GroupVPN or if I use the whack and parse the username & password I get the same, it just flashes a cursor until I cancel it and when I check the ipsec status I get the details pasted below.

If anyone can help me I will be eternally grateful as it means that I wont have to resort to dual booting and having Windoze again.

Mark.

$ sudo ipsec whack --status
000 interface lo/lo ::1
000 interface lo/lo 127.0.0.1
000 interface lo/lo 127.0.0.1
000 interface eth0/eth0 82.32.211.160
000 interface eth0/eth0 82.32.211.160
000 %myid = (none)
000 debug parsing+control
000
000 algorithm ESP encrypt: id=2, name=ESP_DES, ivlen=8, keysizemin=64, keysizemax=64
000 algorithm ESP encrypt: id=3, name=ESP_3DES, ivlen=8, keysizemin=192, keysizemax=192
000 algorithm ESP encrypt: id=7, name=ESP_BLOWFISH, ivlen=8, keysizemin=40, keysizemax=448
000 algorithm ESP encrypt: id=11, name=ESP_NULL, ivlen=0, keysizemin=0, keysizemax=0
000 algorithm ESP encrypt: id=12, name=ESP_AES, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=252, name=ESP_SERPENT, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=253, name=ESP_TWOFISH, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP auth attr: id=1, name=AUTH_ALGORITHM_HMAC_MD5, keysizemin=128, keysizemax=128
000 algorithm ESP auth attr: id=2, name=AUTH_ALGORITHM_HMAC_SHA1, keysizemin=160, keysizemax=160
000 algorithm ESP auth attr: id=5, name=AUTH_ALGORITHM_HMAC_SHA2_256, keysizemin=256, keysizemax=256
000 algorithm ESP auth attr: id=251, name=(null), keysizemin=0, keysizemax=0
000
000 algorithm IKE encrypt: id=5, name=OAKLEY_3DES_CBC, blocksize=8, keydeflen=192
000 algorithm IKE encrypt: id=7, name=OAKLEY_AES_CBC, blocksize=16, keydeflen=128
000 algorithm IKE hash: id=1, name=OAKLEY_MD5, hashsize=16
000 algorithm IKE hash: id=2, name=OAKLEY_SHA1, hashsize=20
000 algorithm IKE dh group: id=2, name=OAKLEY_GROUP_MODP1024, bits=1024
000 algorithm IKE dh group: id=5, name=OAKLEY_GROUP_MODP1536, bits=1536
000 algorithm IKE dh group: id=14, name=OAKLEY_GROUP_MODP2048, bits=2048
000 algorithm IKE dh group: id=15, name=OAKLEY_GROUP_MODP3072, bits=3072
000 algorithm IKE dh group: id=16, name=OAKLEY_GROUP_MODP4096, bits=4096
000 algorithm IKE dh group: id=17, name=OAKLEY_GROUP_MODP6144, bits=6144
000 algorithm IKE dh group: id=18, name=OAKLEY_GROUP_MODP8192, bits=8192
000
000 stats db_ops.c: {curr_cnt, total_cnt, maxsz} :context={0,2,36} trans={0,2,336} attrs={0,2,224}
000
000 "GroupVPN": 82.32.208.0/21===82.32.211.160[@GroupVPN,XC+S=C]...195.147.36.67[@0006B10CC5D0,XS+S=C]===10.0.0.0/24; prospective erouted; eroute owner: #0
000 "GroupVPN":     srcip=unset; dstip=unset; srcup=ipsec _updown; dstup=ipsec _updown;
000 "GroupVPN":   ike_life: 3600s; ipsec_life: 28800s; rekey_margin: 540s; rekey_fuzz: 100%; keyingtries: 0
000 "GroupVPN":   policy: PSK+ENCRYPT+TUNNEL+UP+AGGRESSIVE; prio: 21,24; interface: eth0;
000 "GroupVPN":   newest ISAKMP SA: #0; newest IPsec SA: #0;
000 "GroupVPN":   IKE algorithms wanted: 5_000-2-5, 5_000-2-2, flags=-strict
000 "GroupVPN":   IKE algorithms found:  5_192-2_160-5, 5_192-2_160-2,
000 "GroupVPN":   ESP algorithms wanted: 3_000-2, flags=-strict
000 "GroupVPN":   ESP algorithms loaded: 3_000-2, flags=-strict
000
000 #1: "GroupVPN":500 STATE_AGGR_I1 (sent AI1, expecting AR1); EVENT_RETRANSMIT in 38s; nodpd
000 #1: pending Phase 2 for "GroupVPN" replacing #0
000 #1: pending Phase 2 for "GroupVPN" replacing #0
000

---

### Post by RickKnight on 2007-06-13
Have you been able to solve this problem?

Thanks,
Rick Knight

---

