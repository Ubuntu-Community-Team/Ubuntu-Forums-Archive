---
title: "Autumn leaves error help please"
date: 2008-05-09
forum: General Help
---

### Post by redserpent7 on 2008-05-09
I've been trying to install the autumn leaves effect as shown in this thread:
[URL="http://ubuntuforums.org/showthread.php?p=3792520"]
http://ubuntuforums.org/showthread.php?p=3792520[/URL]

unfortunately I keep getting this error message in the terminal whenever I try to bash the files:

> autumn.c:289: warning: nested extern declaration of ‘glCallList’
autumn.c:289: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:300: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:306: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:314: warning: implicit declaration of function ‘disableTexture’
autumn.c:314: warning: nested extern declaration of ‘disableTexture’
autumn.c:314: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:319: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:320: error: dereferencing pointer to incomplete type
autumn.c:326: error: ‘LeafScreen’ has no member named ‘displayList’
autumn.c:333: error: ‘GL_REPLACE’ undeclared (first use in this function)
autumn.c:334: error: dereferencing pointer to incomplete type
autumn.c:336: warning: implicit declaration of function ‘glDisable’
autumn.c:336: warning: nested extern declaration of ‘glDisable’
autumn.c:337: warning: implicit declaration of function ‘glBlendFunc’
autumn.c:337: warning: nested extern declaration of ‘glBlendFunc’
autumn.c:337: error: ‘GL_ONE’ undeclared (first use in this function)
autumn.c:337: error: ‘GL_ONE_MINUS_SRC_ALPHA’ undeclared (first use in this function)
autumn.c: At top level:
autumn.c:345: warning: type defaults to ‘int’ in declaration of ‘ScreenPaintAttrib’
autumn.c:345: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
autumn.c:379: warning: type defaults to ‘int’ in declaration of ‘CompTransform’
autumn.c:379: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
autumn.c: In function ‘initiateLeaf’:
autumn.c:407: error: dereferencing pointer to incomplete type
autumn.c:409: error: dereferencing pointer to incomplete type
autumn.c:412: error: dereferencing pointer to incomplete type
autumn.c:418: error: dereferencing pointer to incomplete type
autumn.c:420: error: dereferencing pointer to incomplete type
autumn.c:420: error: dereferencing pointer to incomplete type
autumn.c:424: error: dereferencing pointer to incomplete type
autumn.c:424: error: dereferencing pointer to incomplete type
autumn.c:426: error: dereferencing pointer to incomplete type
autumn.c:432: error: dereferencing pointer to incomplete type
autumn.c:439: error: dereferencing pointer to incomplete type
autumn.c: In function ‘setLeafTexture’:
autumn.c:449: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:450: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:450: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c: In function ‘updateLeafTextures’:
autumn.c:457: error: dereferencing pointer to incomplete type
autumn.c:458: error: dereferencing pointer to incomplete type
autumn.c:461: error: dereferencing pointer to incomplete type
autumn.c:461: error: dereferencing pointer to incomplete type
autumn.c:462: error: dereferencing pointer to incomplete type
autumn.c:464: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:466: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:468: warning: implicit declaration of function ‘finiTexture’
autumn.c:468: warning: nested extern declaration of ‘finiTexture’
autumn.c:468: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:469: warning: implicit declaration of function ‘glDeleteLists’
autumn.c:469: warning: nested extern declaration of ‘glDeleteLists’
autumn.c:469: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:472: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:473: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:474: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:476: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:480: error: ‘CompMatrix’ undeclared (first use in this function)
autumn.c:480: error: ‘mat’ undeclared (first use in this function)
autumn.c:483: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:484: warning: implicit declaration of function ‘readImageToTexture’
autumn.c:484: warning: nested extern declaration of ‘readImageToTexture’
autumn.c:484: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:485: error: invalid use of undefined type ‘union _CompOptionValue’
autumn.c:485: error: dereferencing pointer to incomplete type
autumn.c:486: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:487: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:488: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:490: warning: implicit declaration of function ‘compLogMessage’
autumn.c:490: warning: nested extern declaration of ‘compLogMessage’
autumn.c:490: error: dereferencing pointer to incomplete type
autumn.c:490: error: ‘CompLogLevelWarn’ undeclared (first use in this function)
autumn.c:491: error: invalid use of undefined type ‘union _CompOptionValue’
autumn.c:491: error: dereferencing pointer to incomplete type
autumn.c:494: error: dereferencing pointer to incomplete type
autumn.c:494: error: ‘CompLogLevelInfo’ undeclared (first use in this function)
autumn.c:495: error: invalid use of undefined type ‘union _CompOptionValue’
autumn.c:495: error: dereferencing pointer to incomplete type
autumn.c:497: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:498: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:500: error: ‘LeafTexture’ has no member named ‘dList’
autumn.c:501: error: ‘LeafTexture’ has no member named ‘dList’
autumn.c:501: error: ‘GL_COMPILE’ undeclared (first use in this function)
autumn.c:503: error: ‘GL_QUADS’ undeclared (first use in this function)
autumn.c:505: warning: implicit declaration of function ‘glTexCoord2f’
autumn.c:505: warning: nested extern declaration of ‘glTexCoord2f’
autumn.c:505: warning: implicit declaration of function ‘COMP_TEX_COORD_X’
autumn.c:505: warning: nested extern declaration of ‘COMP_TEX_COORD_X’
autumn.c:505: warning: implicit declaration of function ‘COMP_TEX_COORD_Y’
autumn.c:505: warning: nested extern declaration of ‘COMP_TEX_COORD_Y’
autumn.c:506: warning: implicit declaration of function ‘glVertex2f’
autumn.c:506: warning: nested extern declaration of ‘glVertex2f’
autumn.c:508: error: ‘LeafTexture’ has no member named ‘height’
autumn.c:509: error: ‘LeafTexture’ has no member named ‘height’
autumn.c:509: error: ‘LeafTexture’ has no member named ‘width’
autumn.c:510: error: ‘LeafTexture’ has no member named ‘width’
autumn.c:511: error: ‘LeafTexture’ has no member named ‘height’
autumn.c:512: error: ‘LeafTexture’ has no member named ‘height’
autumn.c:512: error: ‘LeafTexture’ has no member named ‘width’
autumn.c:513: error: ‘LeafTexture’ has no member named ‘width’
autumn.c:523: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:525: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:525: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c: In function ‘autumnInitScreen’:
autumn.c:536: error: dereferencing pointer to incomplete type
autumn.c:539: error: dereferencing pointer to incomplete type
autumn.c:543: error: dereferencing pointer to incomplete type
autumn.c:546: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:547: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:548: error: ‘FALSE’ undeclared (first use in this function)
autumn.c:549: error: ‘LeafScreen’ has no member named ‘displayListNeedsUpdate’
autumn.c:551: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:563: warning: implicit declaration of function ‘WRAP’
autumn.c:563: warning: nested extern declaration of ‘WRAP’
autumn.c:563: error: ‘paintOutput’ undeclared (first use in this function)
autumn.c:563: error: ‘autumnPaintOutput’ undeclared (first use in this function)
autumn.c:564: error: ‘drawWindow’ undeclared (first use in this function)
autumn.c:564: error: ‘autumnDrawWindow’ undeclared (first use in this function)
autumn.c:566: error: dereferencing pointer to incomplete type
autumn.c:569: error: ‘TRUE’ undeclared (first use in this function)
autumn.c:570: warning: control reaches end of non-void function
autumn.c: In function ‘autumnFiniScreen’:
autumn.c:578: error: dereferencing pointer to incomplete type
autumn.c:578: error: dereferencing pointer to incomplete type
autumn.c:583: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:585: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:586: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:589: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:590: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:592: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:593: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:595: warning: implicit declaration of function ‘UNWRAP’
autumn.c:595: warning: nested extern declaration of ‘UNWRAP’
autumn.c:595: error: ‘paintOutput’ undeclared (first use in this function)
autumn.c:596: error: ‘drawWindow’ undeclared (first use in this function)
autumn.c: In function ‘autumnDisplayOptionChanged’:
autumn.c:606: error: dereferencing pointer to incomplete type
autumn.c:614: error: dereferencing pointer to incomplete type
autumn.c:614: error: dereferencing pointer to incomplete type
autumn.c:616: error: dereferencing pointer to incomplete type
autumn.c:616: error: dereferencing pointer to incomplete type
autumn.c:617: error: ‘LeafScreen’ has no member named ‘displayListNeedsUpdate’
autumn.c:617: error: ‘TRUE’ undeclared (first use in this function)
autumn.c:626: error: dereferencing pointer to incomplete type
autumn.c:626: error: dereferencing pointer to incomplete type
autumn.c:628: error: dereferencing pointer to incomplete type
autumn.c:628: error: dereferencing pointer to incomplete type
autumn.c:645: error: dereferencing pointer to incomplete type
autumn.c:645: error: dereferencing pointer to incomplete type
autumn.c:647: error: dereferencing pointer to incomplete type
autumn.c:647: error: dereferencing pointer to incomplete type
autumn.c:648: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:648: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:650: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:668: error: dereferencing pointer to incomplete type
autumn.c:669: error: dereferencing pointer to incomplete type
autumn.c:671: error: dereferencing pointer to incomplete type
autumn.c:671: error: dereferencing pointer to incomplete type
autumn.c: In function ‘autumnInitDisplay’:
autumn.c:689: warning: implicit declaration of function ‘allocateScreenPrivateIndex’
autumn.c:689: warning: nested extern declaration of ‘allocateScreenPrivateIndex’
autumn.c:693: error: ‘FALSE’ undeclared (first use in this function)
autumn.c:696: error: too many arguments to function ‘autumnSetToggleInitiate’
autumn.c:703: error: dereferencing pointer to incomplete type
autumn.c:704: error: dereferencing pointer to incomplete type
autumn.c:706: error: dereferencing pointer to incomplete type
autumn.c:708: error: ‘TRUE’ undeclared (first use in this function)
autumn.c:709: warning: control reaches end of non-void function
autumn.c: In function ‘autumnFiniDisplay’:
autumn.c:715: error: dereferencing pointer to incomplete type
autumn.c:717: warning: implicit declaration of function ‘freeScreenPrivateIndex’
autumn.c:717: warning: nested extern declaration of ‘freeScreenPrivateIndex’
autumn.c: In function ‘autumnInit’:
autumn.c:724: warning: implicit declaration of function ‘allocateDisplayPrivateIndex’
autumn.c:724: warning: nested extern declaration of ‘allocateDisplayPrivateIndex’
autumn.c:726: error: ‘FALSE’ undeclared (first use in this function)
autumn.c:728: error: ‘TRUE’ undeclared (first use in this function)
autumn.c:729: warning: control reaches end of non-void function
autumn.c: In function ‘autumnFini’:
autumn.c:734: warning: implicit declaration of function ‘freeDisplayPrivateIndex’
autumn.c:734: warning: nested extern declaration of ‘freeDisplayPrivateIndex’
autumn.c: In function ‘autumnGetVersion’:
autumn.c:741: error: ‘ABIVERSION’ undeclared (first use in this function)
autumn.c:742: warning: control reaches end of non-void function
autumn.c: At top level:
autumn.c:744: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘autumnVTable’
autumn.c:762: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make: *** [build/autumn.lo] Error 1
compiling : autumn.c -> build/autumn.loIn file included from autumn.c:43:
build/autumn_options.h:19: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/autumn_options.h:96: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/autumn_options.h:108: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/autumn_options.h:109: error: expected declaration specifiers or ‘...’ before ‘CompActionCallBackProc’
build/autumn_options.h:110: error: expected declaration specifiers or ‘...’ before ‘CompActionCallBackProc’
autumn.c:74: error: expected specifier-qualifier-list before ‘CompTexture’
autumn.c:101: error: expected specifier-qualifier-list before ‘PaintOutputProc’
autumn.c: In function ‘autumnThink’:
autumn.c:123: error: dereferencing pointer to incomplete type
autumn.c:125: error: dereferencing pointer to incomplete type
autumn.c:127: error: dereferencing pointer to incomplete type
autumn.c:128: error: dereferencing pointer to incomplete type
autumn.c:133: error: dereferencing pointer to incomplete type
autumn.c: In function ‘stepLeafPositions’:
autumn.c:157: error: dereferencing pointer to incomplete type
autumn.c:157: error: dereferencing pointer to incomplete type
autumn.c:160: error: ‘TRUE’ undeclared (first use in this function)
autumn.c:160: error: (Each undeclared identifier is reported only once
autumn.c:160: error: for each function it appears in.)
autumn.c:162: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:163: error: dereferencing pointer to incomplete type
autumn.c:164: error: dereferencing pointer to incomplete type
autumn.c:173: error: dereferencing pointer to incomplete type
autumn.c:173: error: dereferencing pointer to incomplete type
autumn.c:175: error: dereferencing pointer to incomplete type
autumn.c:175: error: ‘CompWindowTypeDesktopMask’ undeclared (first use in this function)
autumn.c:176: warning: implicit declaration of function ‘addWindowDamage’
autumn.c:176: warning: nested extern declaration of ‘addWindowDamage’
autumn.c:180: warning: implicit declaration of function ‘damageScreen’
autumn.c:180: warning: nested extern declaration of ‘damageScreen’
autumn.c:183: warning: control reaches end of non-void function
autumn.c: At top level:
autumn.c:187: error: expected declaration specifiers or ‘...’ before ‘CompAction’
autumn.c:188: error: expected declaration specifiers or ‘...’ before ‘CompActionState’
autumn.c: In function ‘autumnToggle’:
autumn.c:195: warning: implicit declaration of function ‘getIntOptionNamed’
autumn.c:195: warning: nested extern declaration of ‘getIntOptionNamed’
autumn.c:196: warning: implicit declaration of function ‘findScreenAtDisplay’
autumn.c:196: warning: nested extern declaration of ‘findScreenAtDisplay’
autumn.c:196: warning: assignment makes pointer from integer without a cast
autumn.c:200: error: dereferencing pointer to incomplete type
autumn.c:200: error: dereferencing pointer to incomplete type
autumn.c:206: error: ‘TRUE’ undeclared (first use in this function)
autumn.c:207: warning: control reaches end of non-void function
autumn.c: In function ‘setupDisplayList’:
autumn.c:231: error: dereferencing pointer to incomplete type
autumn.c:233: error: ‘LeafScreen’ has no member named ‘displayList’
autumn.c:233: warning: implicit declaration of function ‘glGenLists’
autumn.c:233: warning: nested extern declaration of ‘glGenLists’
autumn.c:235: warning: implicit declaration of function ‘glNewList’
autumn.c:235: warning: nested extern declaration of ‘glNewList’
autumn.c:235: error: ‘LeafScreen’ has no member named ‘displayList’
autumn.c:235: error: ‘GL_COMPILE’ undeclared (first use in this function)
autumn.c:236: warning: implicit declaration of function ‘glBegin’
autumn.c:236: warning: nested extern declaration of ‘glBegin’
autumn.c:236: error: ‘GL_QUADS’ undeclared (first use in this function)
autumn.c:238: warning: implicit declaration of function ‘glColor4f’
autumn.c:238: warning: nested extern declaration of ‘glColor4f’
autumn.c:239: warning: implicit declaration of function ‘glVertex3f’
autumn.c:239: warning: nested extern declaration of ‘glVertex3f’
autumn.c:247: warning: implicit declaration of function ‘glEnd’
autumn.c:247: warning: nested extern declaration of ‘glEnd’
autumn.c:248: warning: implicit declaration of function ‘glEndList’
autumn.c:248: warning: nested extern declaration of ‘glEndList’
autumn.c: In function ‘beginRendering’:
autumn.c:256: error: dereferencing pointer to incomplete type
autumn.c:257: warning: implicit declaration of function ‘glEnable’
autumn.c:257: warning: nested extern declaration of ‘glEnable’
autumn.c:257: error: ‘GL_BLEND’ undeclared (first use in this function)
autumn.c:259: warning: implicit declaration of function ‘glTexEnvf’
autumn.c:259: warning: nested extern declaration of ‘glTexEnvf’
autumn.c:259: error: ‘GL_TEXTURE_ENV’ undeclared (first use in this function)
autumn.c:259: error: ‘GL_TEXTURE_ENV_MODE’ undeclared (first use in this function)
autumn.c:259: error: ‘GL_MODULATE’ undeclared (first use in this function)
autumn.c:261: error: ‘LeafScreen’ has no member named ‘displayListNeedsUpdate’
autumn.c:264: error: ‘LeafScreen’ has no member named ‘displayListNeedsUpdate’
autumn.c:264: error: ‘FALSE’ undeclared (first use in this function)
autumn.c:268: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:268: error: dereferencing pointer to incomplete type
autumn.c:272: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:274: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:275: error: dereferencing pointer to incomplete type
autumn.c:276: error: dereferencing pointer to incomplete type
autumn.c:278: warning: implicit declaration of function ‘enableTexture’
autumn.c:278: warning: nested extern declaration of ‘enableTexture’
autumn.c:278: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:279: error: ‘COMP_TEXTURE_FILTER_GOOD’ undeclared (first use in this function)
autumn.c:283: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:285: warning: implicit declaration of function ‘glTranslatef’
autumn.c:285: warning: nested extern declaration of ‘glTranslatef’
autumn.c:288: warning: implicit declaration of function ‘glRotatef’
autumn.c:288: warning: nested extern declaration of ‘glRotatef’
autumn.c:289: warning: implicit declaration of function ‘glCallList’
autumn.c:289: warning: nested extern declaration of ‘glCallList’
autumn.c:289: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:300: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:306: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:314: warning: implicit declaration of function ‘disableTexture’
autumn.c:314: warning: nested extern declaration of ‘disableTexture’
autumn.c:314: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:319: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:320: error: dereferencing pointer to incomplete type
autumn.c:326: error: ‘LeafScreen’ has no member named ‘displayList’
autumn.c:333: error: ‘GL_REPLACE’ undeclared (first use in this function)
autumn.c:334: error: dereferencing pointer to incomplete type
autumn.c:336: warning: implicit declaration of function ‘glDisable’
autumn.c:336: warning: nested extern declaration of ‘glDisable’
autumn.c:337: warning: implicit declaration of function ‘glBlendFunc’
autumn.c:337: warning: nested extern declaration of ‘glBlendFunc’
autumn.c:337: error: ‘GL_ONE’ undeclared (first use in this function)
autumn.c:337: error: ‘GL_ONE_MINUS_SRC_ALPHA’ undeclared (first use in this function)
autumn.c: At top level:
autumn.c:345: warning: type defaults to ‘int’ in declaration of ‘ScreenPaintAttrib’
autumn.c:345: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
autumn.c:379: warning: type defaults to ‘int’ in declaration of ‘CompTransform’
autumn.c:379: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
autumn.c: In function ‘initiateLeaf’:
autumn.c:407: error: dereferencing pointer to incomplete type
autumn.c:409: error: dereferencing pointer to incomplete type
autumn.c:412: error: dereferencing pointer to incomplete type
autumn.c:418: error: dereferencing pointer to incomplete type
autumn.c:420: error: dereferencing pointer to incomplete type
autumn.c:420: error: dereferencing pointer to incomplete type
autumn.c:424: error: dereferencing pointer to incomplete type
autumn.c:424: error: dereferencing pointer to incomplete type
autumn.c:426: error: dereferencing pointer to incomplete type
autumn.c:432: error: dereferencing pointer to incomplete type
autumn.c:439: error: dereferencing pointer to incomplete type
autumn.c: In function ‘setLeafTexture’:
autumn.c:449: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:450: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:450: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c: In function ‘updateLeafTextures’:
autumn.c:457: error: dereferencing pointer to incomplete type
autumn.c:458: error: dereferencing pointer to incomplete type
autumn.c:461: error: dereferencing pointer to incomplete type
autumn.c:461: error: dereferencing pointer to incomplete type
autumn.c:462: error: dereferencing pointer to incomplete type
autumn.c:464: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:466: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:468: warning: implicit declaration of function ‘finiTexture’
autumn.c:468: warning: nested extern declaration of ‘finiTexture’
autumn.c:468: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:469: warning: implicit declaration of function ‘glDeleteLists’
autumn.c:469: warning: nested extern declaration of ‘glDeleteLists’
autumn.c:469: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:472: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:473: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:474: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:476: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:480: error: ‘CompMatrix’ undeclared (first use in this function)
autumn.c:480: error: ‘mat’ undeclared (first use in this function)
autumn.c:483: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:484: warning: implicit declaration of function ‘readImageToTexture’
autumn.c:484: warning: nested extern declaration of ‘readImageToTexture’
autumn.c:484: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:485: error: invalid use of undefined type ‘union _CompOptionValue’
autumn.c:485: error: dereferencing pointer to incomplete type
autumn.c:486: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:487: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:488: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:490: warning: implicit declaration of function ‘compLogMessage’
autumn.c:490: warning: nested extern declaration of ‘compLogMessage’
autumn.c:490: error: dereferencing pointer to incomplete type
autumn.c:490: error: ‘CompLogLevelWarn’ undeclared (first use in this function)
autumn.c:491: error: invalid use of undefined type ‘union _CompOptionValue’
autumn.c:491: error: dereferencing pointer to incomplete type
autumn.c:494: error: dereferencing pointer to incomplete type
autumn.c:494: error: ‘CompLogLevelInfo’ undeclared (first use in this function)
autumn.c:495: error: invalid use of undefined type ‘union _CompOptionValue’
autumn.c:495: error: dereferencing pointer to incomplete type
autumn.c:497: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:498: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:500: error: ‘LeafTexture’ has no member named ‘dList’
autumn.c:501: error: ‘LeafTexture’ has no member named ‘dList’
autumn.c:501: error: ‘GL_COMPILE’ undeclared (first use in this function)
autumn.c:503: error: ‘GL_QUADS’ undeclared (first use in this function)
autumn.c:505: warning: implicit declaration of function ‘glTexCoord2f’
autumn.c:505: warning: nested extern declaration of ‘glTexCoord2f’
autumn.c:505: warning: implicit declaration of function ‘COMP_TEX_COORD_X’
autumn.c:505: warning: nested extern declaration of ‘COMP_TEX_COORD_X’
autumn.c:505: warning: implicit declaration of function ‘COMP_TEX_COORD_Y’
autumn.c:505: warning: nested extern declaration of ‘COMP_TEX_COORD_Y’
autumn.c:506: warning: implicit declaration of function ‘glVertex2f’
autumn.c:506: warning: nested extern declaration of ‘glVertex2f’
autumn.c:508: error: ‘LeafTexture’ has no member named ‘height’
autumn.c:509: error: ‘LeafTexture’ has no member named ‘height’
autumn.c:509: error: ‘LeafTexture’ has no member named ‘width’
autumn.c:510: error: ‘LeafTexture’ has no member named ‘width’
autumn.c:511: error: ‘LeafTexture’ has no member named ‘height’
autumn.c:512: error: ‘LeafTexture’ has no member named ‘height’
autumn.c:512: error: ‘LeafTexture’ has no member named ‘width’
autumn.c:513: error: ‘LeafTexture’ has no member named ‘width’
autumn.c:523: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:525: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:525: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c: In function ‘autumnInitScreen’:
autumn.c:536: error: dereferencing pointer to incomplete type
autumn.c:539: error: dereferencing pointer to incomplete type
autumn.c:543: error: dereferencing pointer to incomplete type
autumn.c:546: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:547: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:548: error: ‘FALSE’ undeclared (first use in this function)
autumn.c:549: error: ‘LeafScreen’ has no member named ‘displayListNeedsUpdate’
autumn.c:551: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:563: warning: implicit declaration of function ‘WRAP’
autumn.c:563: warning: nested extern declaration of ‘WRAP’
autumn.c:563: error: ‘paintOutput’ undeclared (first use in this function)
autumn.c:563: error: ‘autumnPaintOutput’ undeclared (first use in this function)
autumn.c:564: error: ‘drawWindow’ undeclared (first use in this function)
autumn.c:564: error: ‘autumnDrawWindow’ undeclared (first use in this function)
autumn.c:566: error: dereferencing pointer to incomplete type
autumn.c:569: error: ‘TRUE’ undeclared (first use in this function)
autumn.c:570: warning: control reaches end of non-void function
autumn.c: In function ‘autumnFiniScreen’:
autumn.c:578: error: dereferencing pointer to incomplete type
autumn.c:578: error: dereferencing pointer to incomplete type
autumn.c:583: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:585: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:586: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:589: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:590: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:592: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:593: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:595: warning: implicit declaration of function ‘UNWRAP’
autumn.c:595: warning: nested extern declaration of ‘UNWRAP’
autumn.c:595: error: ‘paintOutput’ undeclared (first use in this function)
autumn.c:596: error: ‘drawWindow’ undeclared (first use in this function)
autumn.c: In function ‘autumnDisplayOptionChanged’:
autumn.c:606: error: dereferencing pointer to incomplete type
autumn.c:614: error: dereferencing pointer to incomplete type
autumn.c:614: error: dereferencing pointer to incomplete type
autumn.c:616: error: dereferencing pointer to incomplete type
autumn.c:616: error: dereferencing pointer to incomplete type
autumn.c:617: error: ‘LeafScreen’ has no member named ‘displayListNeedsUpdate’
autumn.c:617: error: ‘TRUE’ undeclared (first use in this function)
autumn.c:626: error: dereferencing pointer to incomplete type
autumn.c:626: error: dereferencing pointer to incomplete type
autumn.c:628: error: dereferencing pointer to incomplete type
autumn.c:628: error: dereferencing pointer to incomplete type
autumn.c:645: error: dereferencing pointer to incomplete type
autumn.c:645: error: dereferencing pointer to incomplete type
autumn.c:647: error: dereferencing pointer to incomplete type
autumn.c:647: error: dereferencing pointer to incomplete type
autumn.c:648: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:648: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:650: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:668: error: dereferencing pointer to incomplete type
autumn.c:669: error: dereferencing pointer to incomplete type
autumn.c:671: error: dereferencing pointer to incomplete type
autumn.c:671: error: dereferencing pointer to incomplete type
autumn.c: In function ‘autumnInitDisplay’:
autumn.c:689: warning: implicit declaration of function ‘allocateScreenPrivateIndex’
autumn.c:689: warning: nested extern declaration of ‘allocateScreenPrivateIndex’
autumn.c:693: error: ‘FALSE’ undeclared (first use in this function)
autumn.c:696: error: too many arguments to function ‘autumnSetToggleInitiate’
autumn.c:703: error: dereferencing pointer to incomplete type
autumn.c:704: error: dereferencing pointer to incomplete type
autumn.c:706: error: dereferencing pointer to incomplete type
autumn.c:708: error: ‘TRUE’ undeclared (first use in this function)
autumn.c:709: warning: control reaches end of non-void function
autumn.c: In function ‘autumnFiniDisplay’:
autumn.c:715: error: dereferencing pointer to incomplete type
autumn.c:717: warning: implicit declaration of function ‘freeScreenPrivateIndex’
autumn.c:717: warning: nested extern declaration of ‘freeScreenPrivateIndex’
autumn.c: In function ‘autumnInit’:
autumn.c:724: warning: implicit declaration of function ‘allocateDisplayPrivateIndex’
autumn.c:724: warning: nested extern declaration of ‘allocateDisplayPrivateIndex’
autumn.c:726: error: ‘FALSE’ undeclared (first use in this function)
autumn.c:728: error: ‘TRUE’ undeclared (first use in this function)
autumn.c:729: warning: control reaches end of non-void function
autumn.c: In function ‘autumnFini’:
autumn.c:734: warning: implicit declaration of function ‘freeDisplayPrivateIndex’
autumn.c:734: warning: nested extern declaration of ‘freeDisplayPrivateIndex’
autumn.c: In function ‘autumnGetVersion’:
autumn.c:741: error: ‘ABIVERSION’ undeclared (first use in this function)
autumn.c:742: warning: control reaches end of non-void function
autumn.c: At top level:
autumn.c:744: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘autumnVTable’
autumn.c:762: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make: *** [build/autumn.lo] Error 1
Would you like to install the default background (the one shown on YouTube) (yes/no)?  
no




.... any suggestions.....

Help please....

---

### Post by PatrickFisher on 2008-05-14
> **redserpent7 said:**
> I've been trying to install the autumn leaves effect as shown in this thread:
[URL="http://ubuntuforums.org/showthread.php?p=3792520"]
http://ubuntuforums.org/showthread.php?p=3792520[/URL]

unfortunately I keep getting this error message in the terminal whenever I try to bash the files:



.... any suggestions.....

Help please....

None on the snow-like plugins work in Hardy at the moment. I am still trying my hardest to combine them, and if that continues to fail, I will patch up Autumn for you. Cool?

---

### Post by AvengingAngel718 on 2008-05-16
i know the bling isnt the best thing about ubuntu, but i miss all my compiz plugins :( a lot of mine dont work anymore, and autumn was my favorite. i hope it gets fixed soon

and how about firefox 3 not working with any hardly any of the extensions? is mozilla planning on fixing that at any point? i miss my mario theme and cooliris previews :(

---

### Post by PatrickFisher on 2008-05-16
> **AvengingAngel718 said:**
> i know the bling isnt the best thing about ubuntu, but i miss all my compiz plugins :( a lot of mine dont work anymore, and autumn was my favorite. i hope it gets fixed soon

and how about firefox 3 not working with any hardly any of the extensions? is mozilla planning on fixing that at any point? i miss my mario theme and cooliris previews :(


I was looking around last night, and was able to find Fireflies and Snow ported to the latest Compiz 0.7.4. Also, over the last two nights I've put in over ten hours completely rewriting the code I started for Elements (Snow, Autumn, Fireflies, Stars, and a surprise), and the progress amazes even myself. Not to be too hopeful, but I think Elements will be completed, tested, code-reduced and released within two months. So far it's looking like the number of lines will be improved considerably, and the plugin should work better than any of the originals. 

I guess what I'm trying to say is that soon, Autumn, Snow, Firelfies, and Stars will be obselete and you will have ALL the useless bling you could want :)

---

