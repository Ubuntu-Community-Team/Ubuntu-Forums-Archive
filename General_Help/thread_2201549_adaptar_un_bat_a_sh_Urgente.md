---
title: "adaptar un bat a sh Urgente"
date: 2014-01-24
forum: General Help
---

### Post by blackzer0 on 2014-01-24
hola a todo tengo el siguiente problema tengo un programa que se ejecuta con un .bat (archivo por lotes Ms-DOS) pero lo necesito ejecutar en ubuntu server 12.4 este es el  archivo

AuthD.bat
> @echo offcolor f0
title AuthD
echo.
echo Start AuthD Interlude Protected
echo.
:start


java -Dfile.encoding=UTF8 -Xmx128m -XX:+UseSerialGC -XX:+AggressiveOpts -cp ./Java/*;Core.jar br.lunna.loginserver.L2LoginServer


if ERRORLEVEL 2 goto restart
if ERRORLEVEL 1 goto error
goto end
:restart
echo.
echo Admin Restarted ...
ping -n 5 localhost > nul
echo.
goto start
:error
echo.
echo LoginServer terminated abnormaly
ping -n 5 localhost > nul
echo.
goto start
:end
echo.
echo LoginServer terminated
echo.
:question
set choix=q
set /p choix=Restart(r) or Quit(q)
if /i %choix%==r goto start
if /i %choix%==q goto exit
:exit
exit
pause no ayo como arrancarlo alguien meda un idea ???

---

