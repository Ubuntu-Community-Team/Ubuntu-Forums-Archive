---
title: "PSPVC install problems"
date: 2006-11-18
forum: General Help
---

### Post by krazed nun on 2006-11-18
I am trying to install PSPVC so i can encode stuff to mp4. i have tried to install other programs like handbrake and vive, but handbrake wont install and vive wont transcode. I heard PSPVC is awsome, but when ever i try to install it it gives me this: 
```
...xvidff.c:91: error: (Each undeclared identifier is reported only once
xvidff.c:91: error: for each function it appears in.)
xvidff.c:91: error: syntax error before ‘single’
xvidff.c:93: error: ‘xvid_plugin_2pass2_t’ undeclared (first use in this function)
xvidff.c:93: error: syntax error before ‘rc2pass2’
xvidff.c:94: error: ‘xvid_gbl_init_t’ undeclared (first use in this function)
xvidff.c:95: error: ‘xvid_enc_create_t’ undeclared (first use in this function)
xvidff.c:96: error: ‘xvid_enc_plugin_t’ undeclared (first use in this function)
xvidff.c:99: error: ‘XVID_VOP_HALFPEL’ undeclared (first use in this function)
xvidff.c:101: error: ‘XVID_VOP_INTER4V’ undeclared (first use in this function)
xvidff.c:103: error: ‘XVID_VOP_TRELLISQUANT’ undeclared (first use in this function)
xvidff.c:105: error: ‘XVID_VOP_HQACPRED’ undeclared (first use in this function)xvidff.c:107: error: ‘XVID_VOP_GREYSCALE’ undeclared (first use in this function)
xvidff.c:114: error: ‘XVID_ME_EXTSEARCH16’ undeclared (first use in this function)
xvidff.c:114: error: ‘XVID_ME_EXTSEARCH8’ undeclared (first use in this function)
xvidff.c:118: error: ‘XVID_ME_ADVANCEDDIAMOND8’ undeclared (first use in this function)
xvidff.c:119: error: ‘XVID_ME_HALFPELREFINE8’ undeclared (first use in this function)
xvidff.c:120: error: ‘XVID_ME_CHROMA_PVOP’ undeclared (first use in this function)
xvidff.c:120: error: ‘XVID_ME_CHROMA_BVOP’ undeclared (first use in this function)
xvidff.c:126: error: ‘XVID_ME_ADVANCEDDIAMOND16’ undeclared (first use in this function)
xvidff.c:126: error: ‘XVID_ME_HALFPELREFINE16’ undeclared (first use in this function)
xvidff.c:136: error: ‘XVID_VOP_MODEDECISION_RD’ undeclared (first use in this function)
xvidff.c:138: error: ‘XVID_ME_HALFPELREFINE8_RD’ undeclared (first use in this function)
xvidff.c:139: error: ‘XVID_ME_QUARTERPELREFINE8_RD’ undeclared (first use in this function)
xvidff.c:140: error: ‘XVID_ME_EXTSEARCH_RD’ undeclared (first use in this function)
xvidff.c:140: error: ‘XVID_ME_CHECKPREDICTION_RD’ undeclared (first use in this function)
xvidff.c:143: error: ‘XVID_VOP_FAST_MODEDECISION_RD’ undeclared (first use in this function)
xvidff.c:145: error: ‘XVID_ME_HALFPELREFINE16_RD’ undeclared (first use in this function)
xvidff.c:145: error: ‘XVID_ME_QUARTERPELREFINE16_RD’ undeclared (first use in this function)
xvidff.c:154: error: ‘XVID_VOL_GMC’ undeclared (first use in this function)
xvidff.c:155: error: ‘XVID_ME_GME_REFINE’ undeclared (first use in this function)
xvidff.c:158: error: ‘XVID_VOL_QUARTERPEL’ undeclared (first use in this function)
xvidff.c:159: error: ‘XVID_ME_QUARTERPELREFINE16’ undeclared (first use in this function)
xvidff.c:161: error: ‘XVID_ME_QUARTERPELREFINE8’ undeclared (first use in this function)
xvidff.c:164: error: ‘xvid_gbl_init’ undeclared (first use in this function)
xvidff.c:165: error: ‘XVID_VERSION’ undeclared (first use in this function)
xvidff.c:182: warning: implicit declaration of function ‘xvid_global’
xvidff.c:182: error: ‘XVID_GBL_INIT’ undeclared (first use in this function)
xvidff.c:185: error: ‘xvid_enc_create’ undeclared (first use in this function)
xvidff.c:193: error: ‘XVID_PROFILE_S_L3’ undeclared (first use in this function)xvidff.c:200: error: ‘plugins’ undeclared (first use in this function)
xvidff.c:225: error: ‘rc2pass2’ undeclared (first use in this function)
xvidff.c:263: error: ‘xvid_plugin_2pass2’ undeclared (first use in this function)
xvidff.c:268: error: ‘single’ undeclared (first use in this function)
xvidff.c:272: error: ‘xvid_plugin_single’ undeclared (first use in this function)
xvidff.c:279: error: ‘xvid_plugin_lumimasking’ undeclared (first use in this function)
xvidff.c:307: error: ‘XVID_VOL_MPEGQUANT’ undeclared (first use in this function)
xvidff.c:334: error: ‘XVID_GLOBAL_CLOSED_GOP’ undeclared (first use in this function)
xvidff.c:353: error: ‘XVID_GLOBAL_PACKED’ undeclared (first use in this function)
xvidff.c:356: warning: implicit declaration of function ‘xvid_encore’
xvidff.c:356: error: ‘XVID_ENC_CREATE’ undeclared (first use in this function)
xvidff.c: In function ‘ff_xvid_encode_frame’:
xvidff.c:385: error: ‘xvid_enc_frame_t’ undeclared (first use in this function)
xvidff.c:385: error: syntax error before ‘xvid_enc_frame’
xvidff.c:386: error: ‘xvid_enc_stats_t’ undeclared (first use in this function)
xvidff.c:389: error: ‘xvid_enc_frame’ undeclared (first use in this function)
xvidff.c:390: error: ‘XVID_VERSION’ undeclared (first use in this function)
xvidff.c:391: error: ‘xvid_enc_stats’ undeclared (first use in this function)
xvidff.c:405: error: ‘XVID_CSP_PLANAR’ undeclared (first use in this function)
xvidff.c:416: error: ‘XVID_TYPE_AUTO’ undeclared (first use in this function)
xvidff.c:427: error: ‘XVID_ENC_ENCODE’ undeclared (first use in this function)
xvidff.c:444: error: ‘XVID_TYPE_PVOP’ undeclared (first use in this function)
xvidff.c:446: error: ‘XVID_TYPE_BVOP’ undeclared (first use in this function)
xvidff.c:448: error: ‘XVID_TYPE_SVOP’ undeclared (first use in this function)
xvidff.c:452: error: ‘XVID_KEYFRAME’ undeclared (first use in this function)
xvidff.c: In function ‘ff_xvid_encode_close’:
xvidff.c:477: error: ‘XVID_ENC_DESTROY’ undeclared (first use in this function)
xvidff.c: At top level:
xvidff.c:614: error: syntax error before ‘*’ token
xvidff.c: In function ‘xvid_ff_2pass_create’:
xvidff.c:616: error: ‘param’ undeclared (first use in this function)
xvidff.c:621: error: ‘XVID_ERR_FAIL’ undeclared (first use in this function)
xvidff.c:630: warning: implicit declaration of function ‘XVID_VERSION_MAJOR’
xvidff.c:630: error: ‘XVID_VERSION’ undeclared (first use in this function)
xvidff.c:631: warning: implicit declaration of function ‘XVID_VERSION_MINOR’
xvidff.c:632: warning: implicit declaration of function ‘XVID_VERSION_PATCH’
xvidff.c:634: error: ‘handle’ undeclared (first use in this function)
xvidff.c: At top level:
xvidff.c:646: error: syntax error before ‘xvid_plg_destroy_t’
xvidff.c: In function ‘xvid_ff_2pass_destroy’:
xvidff.c:649: error: ‘ref’ undeclared (first use in this function)
xvidff.c: At top level:
xvidff.c:662: error: syntax error before ‘xvid_plg_data_t’
xvidff.c: In function ‘xvid_ff_2pass_before’:
xvidff.c:668: error: ‘param’ undeclared (first use in this function)
xvidff.c:668: error: ‘XVID_ZONE_QUANT’ undeclared (first use in this function)
xvidff.c:675: error: ‘XVID_ME_CHROMA_PVOP’ undeclared (first use in this function)
xvidff.c:676: error: ‘XVID_ME_CHROMA_BVOP’ undeclared (first use in this function)
xvidff.c:677: error: ‘XVID_ME_EXTSEARCH16’ undeclared (first use in this function)
xvidff.c:678: error: ‘XVID_ME_ADVANCEDDIAMOND16’ undeclared (first use in this function)
xvidff.c:679: error: ‘XVID_ME_FAST_MODEINTERPOLATE’ undeclared (first use in this function)
xvidff.c:680: error: ‘XVID_ME_SKIP_DELTASEARCH’ undeclared (first use in this function)
xvidff.c:681: error: ‘XVID_ME_FASTREFINE16’ undeclared (first use in this function)
xvidff.c:682: error: ‘XVID_ME_BFRAME_EARLYSTOP’ undeclared (first use in this function)
xvidff.c:683: error: ‘XVID_VOP_MODEDECISION_RD’ undeclared (first use in this function)
xvidff.c:684: error: ‘XVID_VOP_FAST_MODEDECISION_RD’ undeclared (first use in this function)
xvidff.c:685: error: ‘XVID_VOP_TRELLISQUANT’ undeclared (first use in this function)
xvidff.c:686: error: ‘XVID_VOP_INTER4V’ undeclared (first use in this function)
xvidff.c:687: error: ‘XVID_VOP_HQACPRED’ undeclared (first use in this function)xvidff.c:689: error: ‘XVID_VOL_GMC’ undeclared (first use in this function)
xvidff.c: At top level:
xvidff.c:705: error: syntax error before ‘xvid_plg_data_t’
xvidff.c: In function ‘xvid_ff_2pass_after’:
xvidff.c:706: error: ‘ref’ undeclared (first use in this function)
xvidff.c:712: error: ‘XVID_ERR_FAIL’ undeclared (first use in this function)
xvidff.c:715: error: ‘param’ undeclared (first use in this function)
xvidff.c: In function ‘xvid_ff_2pass’:
xvidff.c:742: error: ‘XVID_PLG_INFO’ undeclared (first use in this function)
xvidff.c:743: error: ‘XVID_PLG_FRAME’ undeclared (first use in this function)
xvidff.c:746: error: ‘XVID_PLG_BEFORE’ undeclared (first use in this function)
xvidff.c:749: error: ‘XVID_PLG_CREATE’ undeclared (first use in this function)
xvidff.c:752: error: ‘XVID_PLG_AFTER’ undeclared (first use in this function)
xvidff.c:755: error: ‘XVID_PLG_DESTROY’ undeclared (first use in this function)
xvidff.c:759: error: ‘XVID_ERR_FAIL’ undeclared (first use in this function)
make[1]: *** [xvidff.o] Error 1
make[1]: Leaving directory `/home/cow/Desktop/psp/work/ffmpeg_051130/libavcodec'make: *** [lib] Error 2
ERROR during compilation or installation of FFMPEG
```

thanks in advance

---

### Post by arj2 on 2006-12-10
For future reference: you need to install the libxvidcore-dev package (and after that, probably libgtk2.0-dev too).

---

