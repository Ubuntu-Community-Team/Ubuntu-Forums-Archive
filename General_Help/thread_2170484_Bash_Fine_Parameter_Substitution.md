---
title: "Bash Fine Parameter Substitution"
date: 2013-08-26
forum: General Help
---

### Post by drmrgd on 2013-08-26
Suppose I have a situation where I have a directory tree with data files containing the same exact name that I want to copy to a new, collected data directory as below (this is an oversimplified example that should expand I think):

```
$ tree .
&#9500;&#9472;&#9472; collectedData
&#9500;&#9472;&#9472; expt1
&#9474;   &#9492;&#9472;&#9472; data.txt
&#9500;&#9472;&#9472; expt10
&#9474;   &#9492;&#9472;&#9472; data.txt
&#9500;&#9472;&#9472; expt2
&#9500;&#9472;&#9472; expt3
&#9474;   &#9492;&#9472;&#9472; data.txt
&#9500;&#9472;&#9472; expt4
&#9500;&#9472;&#9472; expt5
&#9474;   &#9492;&#9472;&#9472; data.txt
&#9500;&#9472;&#9472; expt6
&#9474;   &#9492;&#9472;&#9472; data.txt
&#9500;&#9472;&#9472; expt7
&#9474;   &#9492;&#9472;&#9472; data.txt
&#9500;&#9472;&#9472; expt8
&#9492;&#9472;&#9472; expt9


11 directories, 6 files
```

You'll note that some directories have data in them, and so do not.  In a simplified case like this, I know that I can just iterate over the directories and copy the files to a new location using parameter substitution to rename the files with a more unique name as I go:

```
$ for f in expt*/data.txt; do cp $f collectedData/${f/\//_}; done
```

I suppose in a more complicated case where the data may be different levels deep in the directory tree, I can use some globbing to get around the complexity of the directory structure.  But, I'm wondering how I might be able to use 'find' in this case and use a similar kind of parameter substitution. There have been a few times where I've had to nest some loops to get around the directory structures, and I feel like I can simplify it with a 'find'.  

As the found files are not indexed by '{}' I don't know what I can use to do the substitution.  Maybe I need xargs here, but I can't quite figure out how to make that work either.  

Does anyone know how to go about this, or is the only way to do this with a bash loop over the directories like I show above?

---

### Post by steeldriver on 2013-08-26
Could you just maintain an integer count? something like

```

$ i=1; while read -rd $'\0' f; do b="${f##*/}"; echo cp "$f" "${b%.txt}_${i}.txt"; ((i++)); done < <(find tests -name 'data.txt' -print0)
cp tests/sub3/data.txt data_1.txt
cp tests/sub1/data.txt data_2.txt
cp tests/sub2/data.txt data_3.txt

```

Or do you need the unique name to reflect the original location?

---

### Post by drmrgd on 2013-08-26
> **steeldriver said:**
> Could you just maintain an integer count? something like

```

$ i=1; while read -rd $'\0' f; do b="${f##*/}"; echo cp "$f" "${b%.txt}_${i}.txt"; ((i++)); done < <(find tests -name 'data.txt' -print0)
cp tests/sub3/data.txt data_1.txt
cp tests/sub1/data.txt data_2.txt
cp tests/sub2/data.txt data_3.txt

```

Or do you need the unique name to reflect the original location?

This is an interesting idea.  Some concepts here I'm not 100% familiar with and going to have to dig into a bit.  I didn't mention it, but I did try to redirect the output from find into a loop like that, but I was missing the idea of playing with the record separator like that.  

Unfortunately - and one of the reasons I was trying to get around doing a loop - is that the parent directories are not always so easily iterated through with an index like that.  The only real constant in the equation here is that the data itself is always called the same name.  The rest of the directory structure depends on the experiment name and origin of the data (e.g. instrument name, server name, secondary analysis pipeline identifiers, etc.).

Thanks for the help, though!  I think I may now have a better idea how redirect the output of find with print0 and read.  I'm going to have to play around with this concept a bit more.

---

### Post by steeldriver on 2013-08-26
The example above isn't actually using the index for the directory iteration ('find' descends recursively anyway) - only to construct a sequence of unique filenames to copy to the results to

The print0 and the corresponding -d $'\0' in the read are really just 'niceties' to make sure the loop can handle any filenames you through at it (in particular, names including newlines)

---

### Post by alarme on 2013-08-26
Hi.

This script moves files.  If the name exists at destination directory, appends an numeral at the end of the name, before the extension.
Not tested for names including newlines.
You can run it with the -t modifier to test it (does nothing) -> script -t source target
Comments are in spanish.
I hope it helps.

Cheers.

```
#!/bin/bash -f

# renombra / mueve de origen a destino
# si destino ya existe, intercala numeración
#
# mv+ [ruta/]nombre ruta/[nuevo_nombre]
# mv+ [ruta/]nombre [ruta/]nuevo_nombre
#
# los argumentos deben estar entre comillas dobles
# no se debe emplear la barra invertida como carácter de escape en los argumentos

# análisis mínimo de los argumentos
while case "$1" in
	-t )
		test=1
		shift
		;;
	--help | -h )
		echo "renombra / mueve de origen a destino"
		echo "si destino ya existe, intercala numeración"
		echo
		echo "mv+ [ruta/]nombre ruta/[nuevo_nombre]"
		echo "mv+ [ruta/]nombre [ruta/]nuevo_nombre"
		echo
		echo "los argumentos deben estar entre comillas dobles"
		echo "no se debe emplear la barra invertida como carácter de escape en los argumentos"
		echo "--upper         convierte a mayúsculas"
		echo "--lower         convierte a minúsculas"

		exit 0
		;;

	--upper )
		upper=1
		lower=0
		shift
		;;
	--lower )
		lower=1
		upper=0
		shift
		;;
	*)
		break
		;;
	esac
do
	echo > /dev/null
done

# crea archivo temporal
archivo_temp0=$(mktemp)

obtener_argumentos () {
	# si la cadena contiene la barra, obtiene la ruta, sin barra al final
	{ echo $1 | grep / > /dev/null ; } && ruta_origen=$(echo ${1%/*})/
	# si es nulo, es el directorio actual
	[ "$ruta_origen" == "" ] && ruta_origen="./"

	# si la cadena contiene la barra, obtiene la ruta, sin barra al final
	{ echo $2 | grep / > /dev/null ; } && ruta_destino=$(echo ${2%/*})/
	# si es nulo, es el directorio actual
	[ "$ruta_destino" == "" ] && ruta_destino="./"

	# obtiene el nombre, incluyendo los comodines
	nombre_origen=${1##*/}
	nombre_destino0=${2##*/}

	# separa nombre y extensión
	extension_origen=$(echo "$nombre_origen" | grep -o ".\{5,5\}$" | grep -o "\..*$")
	nombre_origen=$(echo "$nombre_origen" | sed 's/'"$extension_origen"'$//')
	extension_destino0=$(echo "$nombre_destino0" | grep -o ".\{5,5\}$" | grep -o "\..*$")
}

obtener_lista () {
	# generar un fichero con el listado de archivos contenidos en el directorio [ruta/] que se ajustan al patrón 'nombre'
	find "$(echo $ruta_origen)" -maxdepth 1 -name "$(echo $nombre_origen$extension_origen)" > "$archivo_temp0"

	aux_var=$(wc -l "$archivo_temp0")

echo "+++$nombre_destino0+++"
	if [ "$nombre_destino0" != "" ] && [ "${aux_var%% *}" != "1" ]; then
		echo "Ha especificado múltiples archivos de origen pero un solo destino"
		exit 1
	fi
}

nombre_alternativo () {

	Limite=99
	listo=0
	numerador=""

	# eliminar numeración (1 o 2 dígitos)
        # quitar el comentario de la siguiente línea para que elimine numeradores anteriores
	# nombre_destino=$(echo "$nombre_destino" | sed -e 's/ *([0-9]\{1,2\}) *//g')

	# comprueba si existe
	if [ -f "$ruta_destino$nombre_destino$extension_destino" ]; then

		# prueba con distintos numeradores
		for ((numeracion=0; numeracion<=Limite; numeracion++)); do

			# Si el nombre propuesto no existe
			numerador=" ($numeracion)"
			if [ ! -f "$ruta_destino$nombre_destino$numerador$extension_destino" ]; then
				listo=1
				break
			fi
		done

		if [ "$listo" == "0" ]; then
			echo "-- no se ha podido renombrar $ruta_origen$nombre_origen$extension_origen" >&2
			exit 1
		fi
	fi
}

procesar_lista () {
	while read origen
	do
		# si la cadena contiene la barra, obtiene la ruta, sin barra al final
		{ echo $origen | grep / > /dev/null ; } && ruta_origen=$(echo ${origen%/*})/
		# si es nulo, es el directorio actual
		[ "$ruta_origen" == "" ] && ruta_origen="./"
		# obtiene el nombre, incluyendo los comodines
		nombre_origen=${origen##*/}
		# separa nombre y extensión
		extension_origen=$(echo "$nombre_origen" | grep -o ".\{5,5\}$" | grep -o "\..*$")
		nombre_origen=$(echo "$nombre_origen" | sed 's/'"$extension_origen"'$//')

		# asigna valores por defecto
		if [ "$nombre_destino0" == "" ]; then
			nombre_destino="$nombre_origen"
			extension_destino="$extension_origen"
		else
			nombre_destino="$nombre_destino0"
			if [ "$extension_destino0" == "" ]; then
				extension_destino="$extension_origen"
			else
				extension_destino="$extension_destino0"
			fi
		fi

		# si no es un directorio
		if [ ! -d "$ruta_origen$nombre_origen$extension_origen" ]; then

			if [ "$lower" == "1" ]; then
				nombre_destino=$(echo $nombre_origen | sed 'y/ABCDEFGHIJKLMNOPQRSTUVWXYZÑÇÁÉÍÓÚÀÈÌÒÙÄËÏÖÜ/abcdefghijklmnopqrstuvwxyzñçáéíóúàèìòùäëïöü/')
				extension_destino=$(echo $extension_origen | sed 'y/ABCDEFGHIJKLMNOPQRSTUVWXYZÑÇÁÉÍÓÚÀÈÌÒÙÄËÏÖÜ/abcdefghijklmnopqrstuvwxyzñçáéíóúàèìòùäëïöü/')
			elif [ "$upper" == "1" ]; then
				nombre_destino=$(echo $nombre_origen | sed 'y/abcdefghijklmnopqrstuvwxyzñçáéíóúàèìòùäëïöü/ABCDEFGHIJKLMNOPQRSTUVWXYZÑÇÁÉÍÓÚÀÈÌÒÙÄËÏÖÜ/')
				extension_destino=$(echo $extension_origen | sed 'y/abcdefghijklmnopqrstuvwxyzñçáéíóúàèìòùäëïöü/ABCDEFGHIJKLMNOPQRSTUVWXYZÑÇÁÉÍÓÚÀÈÌÒÙÄËÏÖÜ/')
			fi

			# comprobar que el nombre haya cambiado, de lo contrario se destruirá el archivo al moverlo sobre sí mismo
			if [ "$ruta_origen$nombre_origen$extension_origen" != "$ruta_destino$nombre_destino$extension_destino" ]; then

				nombre_alternativo

				if [ "$test" == "1" ]; then
					echo mv "$(echo "$ruta_origen$nombre_origen$extension_origen")" "$(echo "$ruta_destino$nombre_destino$numerador$extension_destino")"
				else
					# echo "(no ejecutando) mv $(echo "$ruta_origen$nombre_origen$extension_origen")" "$(echo "$ruta_destino$nombre_destino$numerador$extension_destino")"
					mv "$(echo "$ruta_origen$nombre_origen$extension_origen")" "$(echo "$ruta_destino$nombre_destino$numerador$extension_destino")"
				fi
			fi
		fi
	done < "$archivo_temp0"
}

# Inicio del script =====================================================================

obtener_argumentos "$1" "$2"
obtener_lista
procesar_lista

# borra archivos temporales
rm "$archivo_temp0"
exit 0

```

---

### Post by drmrgd on 2013-08-26
> **steeldriver said:**
> The example above isn't actually using the index for the directory iteration ('find' descends recursively anyway) - only to construct a sequence of unique filenames to copy to the results to

The print0 and the corresponding -d $'\0' in the read are really just 'niceties' to make sure the loop can handle any filenames you through at it (in particular, names including newlines)

Ahhh, yeah, of course.  I mispoke on that!  

But, in between things today, I had a look, and now I see how that works, and it is exactly what I'm looking for.  I think I had the re-direction wrong when I first attempted it (going to have to bone back up on that I guess!).  Anyway, now that I know how to read the filename into a variable like that, I can easily either use bash substitution to rearrange things or even pipe it to sed or perl to grab out the bits I need.  Something like this should work for a lot of the cases I encounter (using perl as I'm better with those regexes than sed for some stupid reason!):

```

$ while read f; do file=$(echo $f | perl -pe 's/\.\/(.*)\/.*/$1_data.txt/'); echo $file; done < <(find . -name 'data.txt')
expt1_data.txt
expt6_data.txt
expt7_data.txt
expt5_data.txt
expt3_data.txt
expt10_data.txt
```

Or I can even do a double substitution like you did or whatever.  Now that I see the right concept this is going to save me a lot of time in doing double iterations and such.  Thanks Steeldriver!

---

### Post by drmrgd on 2013-08-26
> **alarme said:**
> Hi.

This script moves files.  If the name exists at destination directory, appends an numeral at the end of the name, before the extension.
Not tested for names including newlines.
You can run it with the -t modifier to test it (does nothing) -> script -t source target
Comments are in spanish.
I hope it helps.

Cheers.

```
#!/bin/bash -f

# renombra / mueve de origen a destino
# si destino ya existe, intercala numeración
#
# mv+ [ruta/]nombre ruta/[nuevo_nombre]
# mv+ [ruta/]nombre [ruta/]nuevo_nombre
#
# los argumentos deben estar entre comillas dobles
# no se debe emplear la barra invertida como carácter de escape en los argumentos

# análisis mínimo de los argumentos
while case "$1" in
    -t )
        test=1
        shift
        ;;
    --help | -h )
        echo "renombra / mueve de origen a destino"
        echo "si destino ya existe, intercala numeración"
        echo
        echo "mv+ [ruta/]nombre ruta/[nuevo_nombre]"
        echo "mv+ [ruta/]nombre [ruta/]nuevo_nombre"
        echo
        echo "los argumentos deben estar entre comillas dobles"
        echo "no se debe emplear la barra invertida como carácter de escape en los argumentos"
        echo "--upper         convierte a mayúsculas"
        echo "--lower         convierte a minúsculas"

        exit 0
        ;;

    --upper )
        upper=1
        lower=0
        shift
        ;;
    --lower )
        lower=1
        upper=0
        shift
        ;;
    *)
        break
        ;;
    esac
do
    echo > /dev/null
done

# crea archivo temporal
archivo_temp0=$(mktemp)

obtener_argumentos () {
    # si la cadena contiene la barra, obtiene la ruta, sin barra al final
    { echo $1 | grep / > /dev/null ; } && ruta_origen=$(echo ${1%/*})/
    # si es nulo, es el directorio actual
    [ "$ruta_origen" == "" ] && ruta_origen="./"

    # si la cadena contiene la barra, obtiene la ruta, sin barra al final
    { echo $2 | grep / > /dev/null ; } && ruta_destino=$(echo ${2%/*})/
    # si es nulo, es el directorio actual
    [ "$ruta_destino" == "" ] && ruta_destino="./"

    # obtiene el nombre, incluyendo los comodines
    nombre_origen=${1##*/}
    nombre_destino0=${2##*/}

    # separa nombre y extensión
    extension_origen=$(echo "$nombre_origen" | grep -o ".\{5,5\}$" | grep -o "\..*$")
    nombre_origen=$(echo "$nombre_origen" | sed 's/'"$extension_origen"'$//')
    extension_destino0=$(echo "$nombre_destino0" | grep -o ".\{5,5\}$" | grep -o "\..*$")
}

obtener_lista () {
    # generar un fichero con el listado de archivos contenidos en el directorio [ruta/] que se ajustan al patrón 'nombre'
    find "$(echo $ruta_origen)" -maxdepth 1 -name "$(echo $nombre_origen$extension_origen)" > "$archivo_temp0"

    aux_var=$(wc -l "$archivo_temp0")

echo "+++$nombre_destino0+++"
    if [ "$nombre_destino0" != "" ] && [ "${aux_var%% *}" != "1" ]; then
        echo "Ha especificado múltiples archivos de origen pero un solo destino"
        exit 1
    fi
}

nombre_alternativo () {

    Limite=99
    listo=0
    numerador=""

    # eliminar numeración (1 o 2 dígitos)
        # quitar el comentario de la siguiente línea para que elimine numeradores anteriores
    # nombre_destino=$(echo "$nombre_destino" | sed -e 's/ *([0-9]\{1,2\}) *//g')

    # comprueba si existe
    if [ -f "$ruta_destino$nombre_destino$extension_destino" ]; then

        # prueba con distintos numeradores
        for ((numeracion=0; numeracion<=Limite; numeracion++)); do

            # Si el nombre propuesto no existe
            numerador=" ($numeracion)"
            if [ ! -f "$ruta_destino$nombre_destino$numerador$extension_destino" ]; then
                listo=1
                break
            fi
        done

        if [ "$listo" == "0" ]; then
            echo "-- no se ha podido renombrar $ruta_origen$nombre_origen$extension_origen" >&2
            exit 1
        fi
    fi
}

procesar_lista () {
    while read origen
    do
        # si la cadena contiene la barra, obtiene la ruta, sin barra al final
        { echo $origen | grep / > /dev/null ; } && ruta_origen=$(echo ${origen%/*})/
        # si es nulo, es el directorio actual
        [ "$ruta_origen" == "" ] && ruta_origen="./"
        # obtiene el nombre, incluyendo los comodines
        nombre_origen=${origen##*/}
        # separa nombre y extensión
        extension_origen=$(echo "$nombre_origen" | grep -o ".\{5,5\}$" | grep -o "\..*$")
        nombre_origen=$(echo "$nombre_origen" | sed 's/'"$extension_origen"'$//')

        # asigna valores por defecto
        if [ "$nombre_destino0" == "" ]; then
            nombre_destino="$nombre_origen"
            extension_destino="$extension_origen"
        else
            nombre_destino="$nombre_destino0"
            if [ "$extension_destino0" == "" ]; then
                extension_destino="$extension_origen"
            else
                extension_destino="$extension_destino0"
            fi
        fi

        # si no es un directorio
        if [ ! -d "$ruta_origen$nombre_origen$extension_origen" ]; then

            if [ "$lower" == "1" ]; then
                nombre_destino=$(echo $nombre_origen | sed 'y/ABCDEFGHIJKLMNOPQRSTUVWXYZÑÇÁÉÍÓÚÀÈÌÒÙÄËÏÖÜ/abcdefghijklmnopqrstuvwxyzñçáéíóúàèìòùäëïöü/')
                extension_destino=$(echo $extension_origen | sed 'y/ABCDEFGHIJKLMNOPQRSTUVWXYZÑÇÁÉÍÓÚÀÈÌÒÙÄËÏÖÜ/abcdefghijklmnopqrstuvwxyzñçáéíóúàèìòùäëïöü/')
            elif [ "$upper" == "1" ]; then
                nombre_destino=$(echo $nombre_origen | sed 'y/abcdefghijklmnopqrstuvwxyzñçáéíóúàèìòùäëïöü/ABCDEFGHIJKLMNOPQRSTUVWXYZÑÇÁÉÍÓÚÀÈÌÒÙÄËÏÖÜ/')
                extension_destino=$(echo $extension_origen | sed 'y/abcdefghijklmnopqrstuvwxyzñçáéíóúàèìòùäëïöü/ABCDEFGHIJKLMNOPQRSTUVWXYZÑÇÁÉÍÓÚÀÈÌÒÙÄËÏÖÜ/')
            fi

            # comprobar que el nombre haya cambiado, de lo contrario se destruirá el archivo al moverlo sobre sí mismo
            if [ "$ruta_origen$nombre_origen$extension_origen" != "$ruta_destino$nombre_destino$extension_destino" ]; then

                nombre_alternativo

                if [ "$test" == "1" ]; then
                    echo mv "$(echo "$ruta_origen$nombre_origen$extension_origen")" "$(echo "$ruta_destino$nombre_destino$numerador$extension_destino")"
                else
                    # echo "(no ejecutando) mv $(echo "$ruta_origen$nombre_origen$extension_origen")" "$(echo "$ruta_destino$nombre_destino$numerador$extension_destino")"
                    mv "$(echo "$ruta_origen$nombre_origen$extension_origen")" "$(echo "$ruta_destino$nombre_destino$numerador$extension_destino")"
                fi
            fi
        fi
    done < "$archivo_temp0"
}

# Inicio del script =====================================================================

obtener_argumentos "$1" "$2"
obtener_lista
procesar_lista

# borra archivos temporales
rm "$archivo_temp0"
exit 0

```

Thanks for the script.  It's a lot more complicated that I need (just looking for one liners that are more efficient than what I usually do), but I'll definitely hang on to it in case something like that comes in handy later on.

---

### Post by steeldriver on 2013-08-26
I guess for completeness it's worth mentioning that cp does a very basic version of this 'out of the box', if you use the *--backup=numbered* option e.g.

```


$ find tests -name 'data.txt' -exec cp --verbose --backup=numbered -t . {} +
`tests/sub3/data.txt' -> `./data.txt' (backup: `./data.txt.~1~')
`tests/sub1/data.txt' -> `./data.txt' (backup: `./data.txt.~2~')
`tests/sub2/data.txt' -> `./data.txt' (backup: `./data.txt.~3~')
$ 
$ ls data.*
data.txt  data.txt.~1~  data.txt.~2~  data.txt.~3~

```

It just doesn't give the same control over the renaming sequence (although you could always re-rename after)

---

