---
title: "escputil Does Not Work"
date: 2007-10-06
forum: General Help
---

### Post by Anlace on 2007-10-06
Greetings,

I have been around and around with this issue . . . . help!  I need to be able to check the ink levels in my printer (which has 6 cartridges and ink is now out in one of them, but which one?!).

I have an Epson Stylus Photo R220.  The driver is guten-print.  I am using the alternative Ubuntu installation and KDE (NOT Kubuntu).

Escputil is installed, I get this error when I try to access Ink Levels via Print Manager > Printer > Printer Tools > EPSON Inkjet:

[INDENT]Operation terminated with errors.[/INDENT]

[INDENT]Cannot open /Stylus Photo R220 read/write: No such file or directory"[/INDENT]

I have used the terminal to access escputil with the command:

[INDENT]sudo escputil --ink-level --raw-device /dev/lp0
or
sudo escputil --ink-level --raw-device /dev/usblp0[/INDENT]

It hangs up forever never returning any data at all.

I have tried various other commands as suggested by escputil --help and always get the same error about needing direct access to a RAW printing device.

Help!  This is frustrating and unacceptable.  I really would rather not have to keep a Windows installation on this computer just to check the stupid ink levels!  ARRRG!

Thanks for any and all help I may get with this problem.

Best Regards,
Gail

PS  I also installed mtink but it uses old gimp-print drivers which do not include drivers for my printer.  When I made a best-guess with a different driver it showed ALL the ink levels at 0% which is clearly inaccurate.


Update:

Does this mean I may be getting somewhere?
[INDENT]gail@BlackBox:~$ sudo escputil -r /dev/usblp0 -m r220 -s
Escputil version 5.0.0.99.1, Copyright (C) 2000-2006 Robert Krawitz
Escputil comes with ABSOLUTELY NO WARRANTY; for details type 'escputil -l'
This is free software, and you are welcome to redistribute it
under certain conditions; type 'escputil -l' for details.

Cannot open /dev/usblp0 read/write: Device or resource busy[/INDENT]

Now if I could only figure out what is making an idle printer busy . . . .

---

### Post by Anlace on 2007-10-06
UPDATE:

I did get escputil to work via command line.  Still won't work going through Print Manager.

The thing that caused all this headache was a "bad" USB cable.  I saw a notice during bootup that suggested a bad cable on USB 4, when I swapped cables out it worked fine.  The errant cable is a Belkin USB cable that is about a year old.

Now if it would only work for me through Print Manager, still any information is better than none and escputil gives good info when it works.

Also, to recap, I tried mtink and it wouldn't work because the old gimp-print driver did not include my printer.  I also tried stylus-toolbox and it won't work, it complains about a missing "glade" module and I can't find any support for it online including their web site so I don't have a clue how to make it work.

I sincerely hope this info helps someone out!

Peace,
Gail

---

### Post by ajgreeny on 2007-10-07
Have a look at the following forum thread which covers some of the problems you have at the moment, particularly my post at #8.  It may help.
[http://ubuntuforums.org/showthread.php?t=516146&highlight=hp+printer+ink+level](http://ubuntuforums.org/showthread.php?t=516146&highlight=hp+printer+ink+level)

---

### Post by Anlace on 2007-10-08
Thank you for the reply, I read thorugh your post, please see mine above.

> I tried mtink and it wouldn't work because the old gimp-print driver did not include my printer

mtink requires and exclusively uses gimp-print.

> I also tried stylus-toolbox and it won't work, it complains about a missing "glade" module and I can't find any support for it online including their web site so I don't have a clue how to make it work.

Not a clue as to what the missing module "glade" is or where to find it.

Best Regards,
Gail

---

### Post by ajgreeny on 2007-10-08
Have you actually tried installing the gutenprint drivers etc etc.  I have gimpprint and gutenprint installed without problem and I can certainly use mtink now that I'm in the lpadmin group.  Perhaps it is just your particular printer model that is a problem.

---

### Post by Lacasito on 2008-04-24
Well, time ago I made this script to manage escputil. maybe it can be useful to you.
Comments are in spanish as that is my mother language, but you can translate if you wish.

#!/bin/bash 
# Autor:Lacasito/MiAnTaTa
# Dependencias: escputil, zenity
##*******************************************************************************************#
#                               Case_EpsonTool_Gui   					     #
#                                     Versión 2						     #
#********************************************************************************************#
#
# Este script utiliza el comando escputil para hacer tareas básica de gestión de su impresora
# y le muestra bonitas pantallas que le harán la vida más gradable.
# Está basado en el realizado para línea de comandos por Lacasito.
# Utiliza una composición de bucle case/esac para escoger las opciones y realizar las acciones seleccionadas
# Y varios condicionales if/fi para el control de las decisiones a tomar.
# Para usarlo, cree un lanzador y en la línea de comandos ponga lo siguiente:
# gksudo /ruta/hasta/el/script/ceg.sh
#
# Primero de todo, limpia la pantalla. Esto es una chorrada porque el script se ejecuta con ventanitas
# y tal, pero es una costumbre que tengo: Limpiar la consola antes de nada.
clear

# Se declaran las variables necesarias.
# Primero la que muestra la ventana de selección de opciones disponibles
OPCION=$(zenity  --title "Epson Tool GUI" --list --text "Información de su impresora. Escoja una opción y pulse Aceptar" --radiolist  --column "Opción" --column "#" --column "Descripción" TRUE 1 "Nivel de tinta (Negro, Cian, Magenta y Amarillo)" FALSE 2 "Imprimir patrón de prueba" FALSE 3 "Limpiar cabezal de impresión" FALSE 4 "Marca y modelo de su impresora" FALSE 5 "Información (Ayuda, Modelos disponibles y Licencia)" --width 460 --height 230)

# Si en la ventana de selección pulsamos Cancelar, la aplicación se despide y se cierra.
if [ ${?} != "0" ]; then
	zenity --info --text="¡Que pase buen día...!"
	exit 0
# Si hemos pulsado Aceptar, seguimos...
else
# Declaramos otra variable que necesitamos para poner un fichero temporal 
# donde se guarda la información sobre la ayuda y la licencia de uso de escputil. 
# Este fichero se borrará al final, antes de abandonar el programa.
INFO="/tmp/ceg.txt"
#Bucle Case/esac que controla cada una de las acciones que se escogen desde la ventana de elección de opciones.
case ${OPCION} in
1) sudo escputil -i -qr /dev/lp0 | zenity --text-info --width 530 --height 210;; # Nivel de tinta
2) sudo escputil -n -qr /dev/lp0 | zenity --text-info --width 530 --height 210;; # Imprime página prueba
3) sudo escputil -c -qr /dev/lp0 | zenity --text-info --width 530 --height 210;; # Limpia el cabezal
4) sudo escputil -d -qr /dev/lp0 | zenity --text-info --width 530 --height 210;; # Marca y modelo
5) sudo escputil -h -qr /dev/lp0 > ${INFO}	# El texto de ayuda se envía al fichero temporal 
	echo >> ${INFO}				# esta es una línea en blanco, para separar.
	echo "MODELOS DISPONIBLES" >> ${INFO}	#Título de la siguiente sección
   sudo escputil -M >> ${INFO}			# Muestra los modelos de impresora disponibles
	echo >> ${INFO}				# esta es una línea en blanco, para separar.
	echo "LICENCIA DE USO" >> ${INFO}	#Título de la siguiente sección
   sudo escputil -l /dev/lp0 >> ${INFO}	# El texto de la licencia se envía al fichero temporal
   zenity --text-info --filename=${INFO} --width 640 --height 480;; # Se muestra el fichero temporal creado.
esac
fi

# Una vez terminado el bucle, si se creó el fichero temporal de la opción 5), se borrará. Si no, pues nada.
if [ -e "${INFO}" ]; then
	rm "${INFO}"
fi

zenity --question --text="¿Desea continuar con la aplicación?"
if [ ${?} = "0" ]; then
	${0}
else
# Se muestra un mensaje de despedida
zenity --info --text="¡Que pase buen día...!"
fi

exit 0

---

