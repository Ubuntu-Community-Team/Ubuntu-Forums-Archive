---
title: "Snow not working"
date: 2008-05-09
forum: General Help
---

### Post by redserpent7 on 2008-05-09
I've tried to install the snow plugin for compiz and everything went well until I tried to install it then a list of errors appeared.... this also happens with other similar effects like fireflies: Here is the error report I get:

snow.c:68: error: expected specifier-qualifier-list before ‘CompTexture’
snow.c:95: error: expected specifier-qualifier-list before ‘PaintOutputProc’
snow.c: In function ‘snowThink’:
snow.c:117: error: dereferencing pointer to incomplete type
snow.c:119: error: dereferencing pointer to incomplete type
snow.c:121: error: dereferencing pointer to incomplete type
snow.c:122: error: dereferencing pointer to incomplete type
snow.c:127: error: dereferencing pointer to incomplete type
snow.c: In function ‘stepSnowPositions’:
snow.c:151: error: dereferencing pointer to incomplete type
snow.c:151: error: dereferencing pointer to incomplete type
snow.c:154: error: ‘TRUE’ undeclared (first use in this function)
snow.c:154: error: (Each undeclared identifier is reported only once
snow.c:154: error: for each function it appears in.)
snow.c:156: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:157: error: dereferencing pointer to incomplete type
snow.c:158: error: dereferencing pointer to incomplete type
snow.c:167: error: dereferencing pointer to incomplete type
snow.c:167: error: dereferencing pointer to incomplete type
snow.c:169: error: dereferencing pointer to incomplete type
snow.c:169: error: ‘CompWindowTypeDesktopMask’ undeclared (first use in this function)
snow.c:170: warning: implicit declaration of function ‘addWindowDamage’
snow.c:170: warning: nested extern declaration of ‘addWindowDamage’
snow.c:174: warning: implicit declaration of function ‘damageScreen’
snow.c:174: warning: nested extern declaration of ‘damageScreen’
snow.c:177: warning: control reaches end of non-void function
snow.c: At top level:
snow.c:181: error: expected declaration specifiers or ‘...’ before ‘CompAction’
snow.c:182: error: expected declaration specifiers or ‘...’ before ‘CompActionState’
snow.c: In function ‘snowToggle’:
snow.c:189: warning: implicit declaration of function ‘getIntOptionNamed’
snow.c:189: warning: nested extern declaration of ‘getIntOptionNamed’
snow.c:190: warning: implicit declaration of function ‘findScreenAtDisplay’
snow.c:190: warning: nested extern declaration of ‘findScreenAtDisplay’
snow.c:190: warning: assignment makes pointer from integer without a cast
snow.c:194: error: dereferencing pointer to incomplete type
snow.c:194: error: dereferencing pointer to incomplete type
snow.c:200: error: ‘TRUE’ undeclared (first use in this function)
snow.c:201: warning: control reaches end of non-void function
snow.c: In function ‘setupDisplayList’:
snow.c:224: error: dereferencing pointer to incomplete type
snow.c:226: error: ‘SnowScreen’ has no member named ‘displayList’
snow.c:226: warning: implicit declaration of function ‘glGenLists’
snow.c:226: warning: nested extern declaration of ‘glGenLists’
snow.c:228: warning: implicit declaration of function ‘glNewList’
snow.c:228: warning: nested extern declaration of ‘glNewList’
snow.c:228: error: ‘SnowScreen’ has no member named ‘displayList’
snow.c:228: error: ‘GL_COMPILE’ undeclared (first use in this function)
snow.c:229: warning: implicit declaration of function ‘glBegin’
snow.c:229: warning: nested extern declaration of ‘glBegin’
snow.c:229: error: ‘GL_QUADS’ undeclared (first use in this function)
snow.c:231: warning: implicit declaration of function ‘glColor4f’
snow.c:231: warning: nested extern declaration of ‘glColor4f’
snow.c:232: warning: implicit declaration of function ‘glVertex3f’
snow.c:232: warning: nested extern declaration of ‘glVertex3f’
snow.c:240: warning: implicit declaration of function ‘glEnd’
snow.c:240: warning: nested extern declaration of ‘glEnd’
snow.c:241: warning: implicit declaration of function ‘glEndList’
snow.c:241: warning: nested extern declaration of ‘glEndList’
snow.c: In function ‘beginRendering’:
snow.c:248: error: dereferencing pointer to incomplete type
snow.c:249: warning: implicit declaration of function ‘glEnable’
snow.c:249: warning: nested extern declaration of ‘glEnable’
snow.c:249: error: ‘GL_BLEND’ undeclared (first use in this function)
snow.c:251: warning: implicit declaration of function ‘glTexEnvf’
snow.c:251: warning: nested extern declaration of ‘glTexEnvf’
snow.c:251: error: ‘GL_TEXTURE_ENV’ undeclared (first use in this function)
snow.c:251: error: ‘GL_TEXTURE_ENV_MODE’ undeclared (first use in this function)
snow.c:251: error: ‘GL_MODULATE’ undeclared (first use in this function)
snow.c:253: error: ‘SnowScreen’ has no member named ‘displayListNeedsUpdate’
snow.c:256: error: ‘SnowScreen’ has no member named ‘displayListNeedsUpdate’
snow.c:256: error: ‘FALSE’ undeclared (first use in this function)
snow.c:260: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:260: error: dereferencing pointer to incomplete type
snow.c:264: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:266: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:267: error: dereferencing pointer to incomplete type
snow.c:268: error: dereferencing pointer to incomplete type
snow.c:270: warning: implicit declaration of function ‘enableTexture’
snow.c:270: warning: nested extern declaration of ‘enableTexture’
snow.c:270: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:271: error: ‘COMP_TEXTURE_FILTER_GOOD’ undeclared (first use in this function)
snow.c:275: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:277: warning: implicit declaration of function ‘glTranslatef’
snow.c:277: warning: nested extern declaration of ‘glTranslatef’
snow.c:279: warning: implicit declaration of function ‘glRotatef’
snow.c:279: warning: nested extern declaration of ‘glRotatef’
snow.c:280: warning: implicit declaration of function ‘glCallList’
snow.c:280: warning: nested extern declaration of ‘glCallList’
snow.c:280: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:287: warning: implicit declaration of function ‘disableTexture’
snow.c:287: warning: nested extern declaration of ‘disableTexture’
snow.c:287: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:292: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:293: error: dereferencing pointer to incomplete type
snow.c:299: error: ‘SnowScreen’ has no member named ‘displayList’
snow.c:306: error: ‘GL_REPLACE’ undeclared (first use in this function)
snow.c:307: error: dereferencing pointer to incomplete type
snow.c:309: warning: implicit declaration of function ‘glDisable’
snow.c:309: warning: nested extern declaration of ‘glDisable’
snow.c:310: warning: implicit declaration of function ‘glBlendFunc’
snow.c:310: warning: nested extern declaration of ‘glBlendFunc’
snow.c:310: error: ‘GL_ONE’ undeclared (first use in this function)
snow.c:310: error: ‘GL_ONE_MINUS_SRC_ALPHA’ undeclared (first use in this function)
snow.c: At top level:
snow.c:318: warning: type defaults to ‘int’ in declaration of ‘ScreenPaintAttrib’
snow.c:318: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
snow.c:352: warning: type defaults to ‘int’ in declaration of ‘CompTransform’
snow.c:352: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
snow.c: In function ‘initiateSnowFlake’:
snow.c:381: error: dereferencing pointer to incomplete type
snow.c:383: error: dereferencing pointer to incomplete type
snow.c:386: error: dereferencing pointer to incomplete type
snow.c:392: error: dereferencing pointer to incomplete type
snow.c:394: error: dereferencing pointer to incomplete type
snow.c:394: error: dereferencing pointer to incomplete type
snow.c:398: error: dereferencing pointer to incomplete type
snow.c:398: error: dereferencing pointer to incomplete type
snow.c:400: error: dereferencing pointer to incomplete type
snow.c:406: error: dereferencing pointer to incomplete type
snow.c:413: error: dereferencing pointer to incomplete type
snow.c: In function ‘setSnowflakeTexture’:
snow.c:423: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:424: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:424: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c: In function ‘updateSnowTextures’:
snow.c:431: error: dereferencing pointer to incomplete type
snow.c:432: error: dereferencing pointer to incomplete type
snow.c:435: error: dereferencing pointer to incomplete type
snow.c:435: error: dereferencing pointer to incomplete type
snow.c:436: error: dereferencing pointer to incomplete type
snow.c:438: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:440: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:442: warning: implicit declaration of function ‘finiTexture’
snow.c:442: warning: nested extern declaration of ‘finiTexture’
snow.c:442: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:443: warning: implicit declaration of function ‘glDeleteLists’
snow.c:443: warning: nested extern declaration of ‘glDeleteLists’
snow.c:443: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:446: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:447: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:448: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:450: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:454: error: ‘CompMatrix’ undeclared (first use in this function)
snow.c:454: error: ‘mat’ undeclared (first use in this function)
snow.c:457: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:458: warning: implicit declaration of function ‘readImageToTexture’
snow.c:458: warning: nested extern declaration of ‘readImageToTexture’
snow.c:458: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:459: error: invalid use of undefined type ‘union _CompOptionValue’
snow.c:459: error: dereferencing pointer to incomplete type
snow.c:460: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:461: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:462: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:464: warning: implicit declaration of function ‘compLogMessage’
snow.c:464: warning: nested extern declaration of ‘compLogMessage’
snow.c:464: error: dereferencing pointer to incomplete type
snow.c:464: error: ‘CompLogLevelWarn’ undeclared (first use in this function)
snow.c:465: error: invalid use of undefined type ‘union _CompOptionValue’
snow.c:465: error: dereferencing pointer to incomplete type
snow.c:468: error: dereferencing pointer to incomplete type
snow.c:468: error: ‘CompLogLevelInfo’ undeclared (first use in this function)
snow.c:469: error: invalid use of undefined type ‘union _CompOptionValue’
snow.c:469: error: dereferencing pointer to incomplete type
snow.c:471: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:472: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:474: error: ‘SnowTexture’ has no member named ‘dList’
snow.c:475: error: ‘SnowTexture’ has no member named ‘dList’
snow.c:475: error: ‘GL_COMPILE’ undeclared (first use in this function)
snow.c:477: error: ‘GL_QUADS’ undeclared (first use in this function)
snow.c:479: warning: implicit declaration of function ‘glTexCoord2f’
snow.c:479: warning: nested extern declaration of ‘glTexCoord2f’
snow.c:479: warning: implicit declaration of function ‘COMP_TEX_COORD_X’
snow.c:479: warning: nested extern declaration of ‘COMP_TEX_COORD_X’
snow.c:479: warning: implicit declaration of function ‘COMP_TEX_COORD_Y’
snow.c:479: warning: nested extern declaration of ‘COMP_TEX_COORD_Y’
snow.c:480: warning: implicit declaration of function ‘glVertex2f’
snow.c:480: warning: nested extern declaration of ‘glVertex2f’
snow.c:482: error: ‘SnowTexture’ has no member named ‘height’
snow.c:483: error: ‘SnowTexture’ has no member named ‘height’
snow.c:483: error: ‘SnowTexture’ has no member named ‘width’
snow.c:484: error: ‘SnowTexture’ has no member named ‘width’
snow.c:485: error: ‘SnowTexture’ has no member named ‘height’
snow.c:486: error: ‘SnowTexture’ has no member named ‘height’
snow.c:486: error: ‘SnowTexture’ has no member named ‘width’
snow.c:487: error: ‘SnowTexture’ has no member named ‘width’
snow.c:497: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:499: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:499: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c: In function ‘snowInitScreen’:
snow.c:510: error: dereferencing pointer to incomplete type
snow.c:513: error: dereferencing pointer to incomplete type
snow.c:517: error: dereferencing pointer to incomplete type
snow.c:520: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:521: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:522: error: ‘FALSE’ undeclared (first use in this function)
snow.c:523: error: ‘SnowScreen’ has no member named ‘displayListNeedsUpdate’
snow.c:525: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:537: warning: implicit declaration of function ‘WRAP’
snow.c:537: warning: nested extern declaration of ‘WRAP’
snow.c:537: error: ‘paintOutput’ undeclared (first use in this function)
snow.c:537: error: ‘snowPaintOutput’ undeclared (first use in this function)
snow.c:538: error: ‘drawWindow’ undeclared (first use in this function)
snow.c:538: error: ‘snowDrawWindow’ undeclared (first use in this function)
snow.c:540: error: dereferencing pointer to incomplete type
snow.c:543: error: ‘TRUE’ undeclared (first use in this function)
snow.c:544: warning: control reaches end of non-void function
snow.c: In function ‘snowFiniScreen’:
snow.c:552: error: dereferencing pointer to incomplete type
snow.c:552: error: dereferencing pointer to incomplete type
snow.c:557: error: ‘SnowScreen’ has no member named ‘snowTexturesLoaded’
snow.c:559: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:560: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:563: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:564: error: ‘SnowScreen’ has no member named ‘snowTex’
snow.c:566: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:567: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:569: warning: implicit declaration of function ‘UNWRAP’
snow.c:569: warning: nested extern declaration of ‘UNWRAP’
snow.c:569: error: ‘paintOutput’ undeclared (first use in this function)
snow.c:570: error: ‘drawWindow’ undeclared (first use in this function)
snow.c: In function ‘snowDisplayOptionChanged’:
snow.c:580: error: dereferencing pointer to incomplete type
snow.c:588: error: dereferencing pointer to incomplete type
snow.c:588: error: dereferencing pointer to incomplete type
snow.c:590: error: dereferencing pointer to incomplete type
snow.c:590: error: dereferencing pointer to incomplete type
snow.c:591: error: ‘SnowScreen’ has no member named ‘displayListNeedsUpdate’
snow.c:591: error: ‘TRUE’ undeclared (first use in this function)
snow.c:600: error: dereferencing pointer to incomplete type
snow.c:600: error: dereferencing pointer to incomplete type
snow.c:602: error: dereferencing pointer to incomplete type
snow.c:602: error: dereferencing pointer to incomplete type
snow.c:619: error: dereferencing pointer to incomplete type
snow.c:619: error: dereferencing pointer to incomplete type
snow.c:621: error: dereferencing pointer to incomplete type
snow.c:621: error: dereferencing pointer to incomplete type
snow.c:622: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:622: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:624: error: ‘SnowScreen’ has no member named ‘allSnowFlakes’
snow.c:642: error: dereferencing pointer to incomplete type
snow.c:643: error: dereferencing pointer to incomplete type
snow.c:645: error: dereferencing pointer to incomplete type
snow.c:645: error: dereferencing pointer to incomplete type
snow.c: In function ‘snowInitDisplay’:
snow.c:663: warning: implicit declaration of function ‘allocateScreenPrivateIndex’
snow.c:663: warning: nested extern declaration of ‘allocateScreenPrivateIndex’
snow.c:667: error: ‘FALSE’ undeclared (first use in this function)
snow.c:670: error: too many arguments to function ‘snowSetToggleInitiate’
snow.c:677: error: dereferencing pointer to incomplete type
snow.c:678: error: dereferencing pointer to incomplete type
snow.c:680: error: dereferencing pointer to incomplete type
snow.c:682: error: ‘TRUE’ undeclared (first use in this function)
snow.c:683: warning: control reaches end of non-void function
snow.c: In function ‘snowFiniDisplay’:
snow.c:689: error: dereferencing pointer to incomplete type
snow.c:691: warning: implicit declaration of function ‘freeScreenPrivateIndex’
snow.c:691: warning: nested extern declaration of ‘freeScreenPrivateIndex’
snow.c: In function ‘snowInit’:
snow.c:698: warning: implicit declaration of function ‘allocateDisplayPrivateIndex’
snow.c:698: warning: nested extern declaration of ‘allocateDisplayPrivateIndex’
snow.c:700: error: ‘FALSE’ undeclared (first use in this function)
snow.c:702: error: ‘TRUE’ undeclared (first use in this function)
snow.c:703: warning: control reaches end of non-void function
snow.c: In function ‘snowFini’:
snow.c:708: warning: implicit declaration of function ‘freeDisplayPrivateIndex’
snow.c:708: warning: nested extern declaration of ‘freeDisplayPrivateIndex’
snow.c: In function ‘snowGetVersion’:
snow.c:715: error: ‘ABIVERSION’ undeclared (first use in this function)
snow.c:716: warning: control reaches end of non-void function
snow.c: At top level:
snow.c:718: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘snowVTable’
snow.c:736: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make: *** [build/snow.lo] Error 1


how do I make it work I really want those effects ....

---

