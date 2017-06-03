# Titre

## Introduction

### Pourquoi choisir Lua

Lua est un language simple et rapide pour un language de script mais assez complet pour faire des programmes simples et est aussi très utilisé pour des "plug-ins".
En plus il fonctionne sur presque n'importe quelle plate-forme sur PC (comme windows, mac os, linux ou \*BSD), sur téléphone (comme iOS ou android) et même sur des consoles comme les nintendo ds ou les ps2.

###Installation

Dans ce tutoriel j'utiliserai Lua 5.3 (Lua 5.3.4 précisément mais n'importe quelle version 5.3 devrait marcher avec quelques différences mineures) et certaines choses peuvent ne pas fonctionner dans des versions plus anciennes ou plus récentes (si vous lisez ce tutoriel après la sortie de Lua 5.4 (dans ce cas il manquera les nouveautés)).
[Lien de tous les binaires de Lua (pas besoin de compiler)](http://www.lua-users.org/wiki/LuaBinaries).
Si vous voulez ne rien télécharger, vous pouvez aussi essayer [la démo en ligne de Lua](https://www.lua.org/demo.html).

#### Windows

Pour windows vous pouvez trouver des binaires (c'est plutôt compliqué de compiler sur windows) [ici](http://www.luabinaries.sourceforge.net) ou [là](https://sourceforge.net/projects/luabinaries/files/5.3.3/Tools%20Executables/lua-5.3.3_Win32_bin.zip/download) pour le lien de téléchargement direct de Lua 5.3.3 (32 bits).

#### Mac Os

[Le lien que j'ai donné pour windows](http://www.luabinaries.sourceforge.net) contient aussi des binaires pour mac os mais vous pouvez aussi le compiler pour avoir la dernière version en suivant les instructions [sur le site de Lua](https://www.lua.org/download.html).
Je laisse [le lien direct de téléchargement d'un binaire Lua 5.3.2 pour mac os (la version la plus récente disponible actuellement en binaire)](https://sourceforge.net/projects/luabinaries/files/5.3.2/Tools%20Executables/lua-5.3.2_MacOS1011_bin.tar.gz/download)

####Linux

La plupart des distributions auront un paquet Lua dans leur gestionnaire de paquet (même des anciennes versions, par exemple j'ai "_lua52_" pour la dernière version de Lua 5.2 (5.2.4)).
Vous pouvez aussi le compiler comme pour mac os (il y a plus de chances que ça marche d'ailleurs) avec les instructions du [site de Lua](https://www.lua.org/download.html).
Sinon [le lien que j'ai donné pour windows](http://luabinaries.sourceforge.net) marche toujours.
Je ne peux pas donner de lien direct de Lua pour linux parce qu'il y a des versions différentes pour différents kernels mais je laisse au moins le [lien du dossier pour Lua 5.3.3](https://sourceforge.net/projects/luabinaries/files/5.3.3/Tools%20Executables/).

### Utiliser Lua

Une fois que vous avez installé Lua vous pouvez lancer l'interpreteur (il lancera ce que vous tapez automatiquement) en lancant "lua" (ou "lua.exe" pour windows) dans un terminal (il lance parfois automatiquement le terminal (mac os))
Pour ouvrir un terminal sur windows, ouvrez l'explorateur windows dans le dossier qui contient Lua et cliquez droit en enfoncant shift.
Sur linux la plupart des explorateurs de fichiers ont aussi cette fonctionnalité mais si vous avez installé Lua avec un gestionnaire de paquets (ou avec make install après avoir compilé) il suffit d'en ouvrir un n'importe où.
Après avoir ouvert le terminal au bon endroit vous pouvez taper `lua` pour lancer l'interpreteur ou `lua fichier.lua` pour lancer un fichier (dans ce cas un fichier qui s'appelle "fichier.lua").

#### Un éditeur de texte

Pour programmer en Lua dans un fichier, c'est parfois plus simple d'utiliser un éditeur de texte qui colore certaines parties du texte (c'est plus lisible).
Pour windows je recommande [notepad++](https://notepad-plus-plus.org/fr/).
Pour mac os il y a [TextMate](https://macromates.com/) ou [Fraise](https://github.com/jfmoy/Fraise/downloads).
Pour linux vous avez peut-être déja un éditeur pour Lua comme [geany](geany.org), [Kate](https://kate-editor.org/) ou mousepad, sinon, vous pouvez toujours en installer un avec votre gestionnaire de paquets.
Il y a aussi un IDE appelé [Zerobrane Studio](https://studio.zerobrane.com/) (je ne l'ai pas essayé pour l'instant) et un [éditeur Lua pour eclipse](https://eclipse.org/ldt/) (qui est au départ un IDE pour java mais supporte aussi d'autres languages), les deux fonctionnent sur windows, mac os et linux.
Si vous voulez utiliser le même éditeur sur chaque plate-forme sans installer un IDE, il y a aussi [Atom](http://www.atom.io).
Vous pouvez aussi regarder [la liste des éditeurs pour Lua](http://lua-users.org/wiki/LuaEditorSupport).

**NOTE:** Les éditeurs que j'ai cité pour linux peuvent aussi fonctionner sur d'autres plate-formes, ils sont juste plus souvent utilisés pour linux.

## Le premier programme

On va commencer par tradition par le "Hello World!", c'est à dire un programme qui affiche "Hello World!", il y a deux moyens de le faire.

    print("Hello World!")

ou

    io.write("Hello World!")

Il y a quelques différences entre les deux mais on les verra plus tard.
Pour tester ce code, tapez le dans l'interpreteur Lua ou écrivez le dans un fichier et ouvrez le avec lua (`lua fichier.lua`).
Normalement ce code devrait avoir affiché "Hello World!".
Comme vous l'avez remarqué, j'ai mis le texte à afficher entre guillemets, c'est pour préciser que ce n'est pas du code, mais du texte (on verra ça plus en détail dans la partie sur les variables).
`print` et `io.write` servent à afficher du texte (`print` peut aussi afficher d'autres choses, on verra ça aussi avec les variables), c'est ce qu'on appelle des fonctions, qu'on "_appelle_" ("_call_" en anglais) en général (je dis en général parce qu'il y a parfois un autre moyen, j'en parlerai avec les fonctions) avec des parenthèses et des "_arguments_" à l'intérieur (dans ce cas le texte "Hello World!").
Pour donner plusieurs arguments il faudrait les séparer par une virgule (",").

    print("Hello", "World") --> Hello	World

L'espace après la virgule n'est pas necessaire.

Dans un code en Lua qui contient plusieurs "_instructions_", chaque instruction peut être écrite avec ou sans point-virgule à la fin et soit sur une ligne séparée soit sur une autre ligne avec une autre instruction (une ligne peut contenir n'importe quel nombre d'instructions), par exemple, les codes suivants sont équivalents.

    print("Bonjour !")
    print("Comment allez vous !")

    print("Bonjour !");
    print("Comment allez vous !");

    print("Bonjour !"); print("Comment allez vous !")

    print("Bonjour !") print("Comment allez vous !")

Même si la dernière façon est considérée "sale" par certaines personnes.

L'espace entre les deux `print` des deux derniers exemples n'est pas necessaire parce qu'ils se terminent tout les deux par un caractère spécial (ici ")" et ";").

### Les commentaires

Les commentaires sont des morceaux de textes qui ne sont pas executés, en Lua les commentaires commencent par `--` (deux tirets).
Ils sont souvent utilisés pour expliquer un bout de code sans avoir à le relire (surtout si il est compliqué).
Par exemple

    print("Hello World!") --affiche Hello World!

fonctionne de la même façon que la dernière fois même avec le commentaire.
Ce n'est peut-être pas necessaire de mettre des commentaires sur chaque ligne, surtout quand on est habitué à print, mais c'était pour l'exemple.
Il existe aussi des commentaires "_multilignes_" qui commencent par `--[[` et se terminent par `--]]`.
Par exemple

    print("Hello World!")
    --[[
    Affiche Hello World!
    En hommage au premier programme.
    --]]

On peut aussi ajouter un tiret au premier pour décommenter toute la partie qu'il commente, c'est utile pour remettre un code qu'on avait commenté.
Par exemple

    ---[[
    print("Cette partie n'est pas commentée !")
    --]]

Dans ce code les parties `---[[` et `--]]` ne font pas planter parce qu'elles sont commentées par les deux tirets.

## Les variables

Dans cette partie on va parler des variables "_globales_" (il y a aussi des variables locales mais on les verra après).

Une variable permet de stocker une valeur (qui peut être de plusieurs types, on verra ça juste après).
Pour "_définir_" (on peut aussi dire affecter et assigner) une variable globale (plus exactement sa valeur) on donne un nom (par exemple "texte") avec un `=` et la valeur qu'on veut lui attribuer (il peut y avoir des espaces avant et après le `=̀`), par exemple

    texte="Bonjour !"

Après ce code, quand on utilise `print` avec comme argument le nom de la variable (pas entre guillemets, pour préciser que c'est une variable et pas du texte), il affichera "Bonjour !", c'est comme ça qu'on donne la valeur d'une variable en argument.

    print(texte) --> "Bonjour!"

Le nom d'une variable peut être n'importe quel combinaison de lettre majuscules, minuscules, de tiret bas ("\_") et de chiffres (du moment qu'il n'est pas le premier caractère), mais c'est une bonne idée en général de ne pas commencer un nom de variable par un tiret bas et par au moins une lettre minuscule parce que certains noms sont réservés à Lua (comme `_VERSION` qui contient un texte avec la version, comme "Lua 5.3").

On peut déclarer plusieurs variables sur la même ligne de cette façon

    a,b = "arbre","bras"

On peut aussi utiliser cette syntaxe pour inverser deux ou plusieurs variables.

    a,b = "arbre","bras"
    print(a,b) --> arbre	bras
    a,b = b,a
    print(a,b) --> bras	arbre
    x,y,z = "xylophone","yaourt","zèbre"
    print(x,y,z) --> xylophone	yaourt	zèbre
    x,y,z = y,z,x
    print(x,y,z) --> yaourt	zèbre	xylophone

Une variable globale n'a pas besoin d'être "_déclarée_" à l'avance, c'est à dire qu'on peut l'utiliser sans avoir besoin de préciser qu'on veut utiliser le nom (contrairement à la plupart des languages compilés) et on peut redéfinir le type d'une variable en lui "_assignant_" une valeur d'un autre type.

L'interpréteur lua (en tout cas en version 5.3 normalement) affiche les valeurs des variables quand vous entrez leurs noms, ça évite de taper print à chaque fois.

### Les types de variable

Il y a huit types de variables en Lua: les "_nils_", les booléens, les nombres, les "_strings_" (le texte), les "_userdata_", les fonctions, les "_thread_" (tâches), et les "_tables_".

On peut récuperer le type d'une variable avec la fonction `type` avec comme argument la variable, elle "_retourne_" le type en tant que texte.

    print(type("Hello World!")) --> string

#### Les _nils_
Un _nil_ en Lua ne peut avoir qu'une seule valeur (`nil`) et est utilisé quand une variable n'existe pas, par exemple

    print(nomDeVariableQuiNExistePas) --> nil

Ça permet de supprimer une variable, pour que sa valeur soit "_collectée_" (c'est à dire liberer la mémoire qu'elle utilise pour la laisser au système ou aux autres programmes), tout simplement en lui donnant la valeur `nil`.
#### Les nombres
Les nombres sont un des type de variable les plus simple, en Lua il n'y a qu'un seul type de nombre (en fait 2 depuis la version 5.3 mais d'après [le manuel](https://www.lua.org/manual/5.3/manual.html#2.1) le programmeur peut ignorer leur différences).
Pour utiliser un nombre il suffit d'écrire le nombre en chiffres en remplacant la virgule (si il y en a une) par un point.

    n = 59
    print(n) --> 59
    n2 = 25.6
    print(n) --> 25.6
    n3 = -85.1
    print(n3) --> -85.1

##### Les opérateurs
Avoir des nombres serait inutile si on ne pouvait pas faire d'opérations dessus.

Les opérateurs basiques en Lua sont: `+` (addition), `-` (soustraction), `*` (multiplication), `/` (division), `%` ([modulo](https://fr.wikipedia.org/wiki/Modulo_(op%C3%A9ration\))) et `^` (puissance), il y a aussi `//` pour la division de nombre entiers (8/5=1.6 mais 8//5=1) mais c'est plus rare de l'utiliser.

Les opérateurs n'ont aucun effet sur les variables sans utiliser `=`.

    print(5*8) --> 40

    n=59
    n=n+9
    print(n) --> 68

    n=8
    print(8/n) --> 1
    print(n/5) --> 1.6
    print(n) --> 8

Le `-` peut être utilisé en tant qu'opérateur unaire (c'est à dire sur un seul élément au lieu de deux pour les autres) pour inverser le signe d'un nombre.

    n=852
    print(-n) --> -852
    print(n) --> 852
    n=-5
    print(-n) --> 5

##### La fonction tonumber

La fonction `tonumber` permet de convertir explicitement un autre type (notamment du texte) en nombre (elle retourne l'argument si c'est déja un nombre), je dis explicitement parce que du texte peut être utilisé comme nombre sans `tonumber`.

    print(tonumber("58")+8) --> 66
    print("58"+8) --> 66

##### La "_bibliothèque_" math

Ce qu'on appelle une bibliothèque c'est tout simplement un ensemble de fonctions et de constantes qui sont en Lua, rangés dans des _tables_ (qu'on verra plus tard) ce qui permet de les utiliser de cette façon : `nomDeLaBibliotheque.nomDeLaFonction(arguments)`, comme pour `io.write`.

`math.floor`, `math.ceil` et `math.modf` permettent d'arrondir des nombres.

    print(math.floor(5.6)) --> 5
    print(math.floor(5.3)) --> 5
    print(math.floor(-5.4)) --> -6
    print(math.ceil(5.4)) --> 6
    print(math.ceil(5.8)) --> 6
    print(math.ceil(-5.6)) --> -5
    print(math.modf(5.4)) --> 5
    print(math.modf(5.6)) --> 5
    print(math.modf(-5.4)) --> -5
    print(math.modf(-5.6)) --> -5

`math.huge` est une constante représentant le plus grand nombre représentable en Lua.

    print(math.huge) --> inf

Le texte "inf" représente les trois premières lettres de "infinity" (infini en anglais).

`math.pi` est une constante contenant le nombre pi (&#960;).

    print(math.pi) --> 3.1415926535898

`math.deg` et `math.rad` convertissent des radians en degrées et des degrées en radians, respectivement.

    print(math.rad(90)) --> 1.5707963267949
    print(math.deg(math.pi)) --> 180.0

`math.sin`, `math.cos`, `math.tan`, `math.asin`, `math.acos` et `math.atan` représentent les fonctions trigonométriques du même nom, en radians.

    print(math.cos(math.pi)) --> -1.0
    print(math.sin(math.rad(90))) --> 1.0
    print(math.atan(1)*4) --> 3.1415926535898

`math.random` génère un nombre aléatoire par rapport à une "_seed_" (par défaut 1), en utilisant la même _seed_, les nombres seront les mêmes à chaque redémarrage de lua.

 * En utilisant `math.random` sans arguments, il prendra un nombre aléatoire entre 0 et 1 (avec virgule).
 * Avec un argument, il le choisira entre 1 et l'argument donné.
 * Avec deux arguments, le nombre sera entre le premier et le deuxième argument.

`math.randomseed` permet de changer la _seed_ de `math.random`

    print(math.random()) --> 0.84018771676347
    print(math.random()) --> 0.39438292663544
    print(math.random(6)) --> 5
    print(math.random(6)) --> 5
    print(math.random(6)) --> 6
    print(math.random(-50,50)) --> -31
    print(math.random(-50,50)) --> -17
    print(math.random(-50,50)) --> 27
    math.randomseed(58)
    print(math.random()) --> 0.93766735633835

Une technique pour avoir une _seed_ différente à chaque fois est d'utiliser le retour de la fonction `os.time` en argument à randomseed, parce que `os.time` donne le temps, le résultat devrais toujours être différent.

    math.randomseed(os.time())

**NOTE:** Ce n'est pas nécessaire d'utiliser `print` pour appeller des fonctions mais je l'ajoute pour afficher leurs résultats pour ceux qui n'utiliserait pas l'interpreteur.

#### Le texte

Pour utiliser du texte il suffit de l'écrire entre guillemets (`"`) en peut aussi utiliser le caractère `'` ou alors, si le texte fait plusieurs lignes on peut utiliser les "_long strings_", c'est à dire commencer le texte par `[[̀` et le terminer par `]]` (un peu comme pour les commentaires multilignes).

    print("texte1") --> texte1
    print('texte2') --> texte2
    print([[texte
    de
    plusieurs
    lignes]])

On peut aussi utilser du texte multiligne de différents niveaux (`[[` et `]]` étant le niveau 0), les niveaux fonctionnent aussi avec les commentaires multilignes.

    --niveau 1
    print([=[
    print([[texte
    de
    plusieurs
    lignes]])
    ]=])
    --niveau 4
    print([====[
    print([=[texte
    de
    plusieurs
    lignes]=])
    ]====])

Il n'y a aucune différence entre les différents niveaux à part le fait qu'un niveau ne peut se fermer qu'avec le même niveau (niveau 4 avec niveau 4 seulement par exemple), c'est donc utile pour avoir du texte long qui contient du texte long.
En général on décide du caractère (entre `"` et `'`) par rapport au texte (si il y a des guillemets on peut utiliser `'` par exemple).

##### L'échappement

Si on veut utiliser certains caractères qu'on ne peut pas utiliser normalement, on peut utiliser des "_escapes_" qui commencent par un anti-slash (\\).

* \a [caractère d'appel](https://fr.wikipedia.org/wiki/Caract%C3%A8re_d%27appel)
* \b retour arrière
* \f form feed
* \n retour à la ligne
* \r retour chariot
* \t tabulation
* \v tabulation verticale
* \\\\ anti-slash
* \" guillemet
* \' apostrophe

<!-- -->

    print("\"") --> "
    print("\\") --> \
    print("tex\nte")
    --[[même chose que
    [[tex
    te]]
    --]]

##### Les opérateurs sur le texte

En lua il y a deux opérateurs pour le texte: `..` pour la concaténation (mettre du texte à la suite d'un autre) et l'opérateur unaire `#` pour connaitre la longueur du texte (pour le texte avec des caractères non anglais il y a une fonction expliquée à la fin du chapitre "La "bibliothèque" string").

    print("1".."2") --> 12

    print(#"texte") --> 5
    t = "texte2"
    print(#t) --> 6

##### La fonction tostring

La fonction `tostring` permet de convertir d'autre types de variables en texte (print utilise tostring sur chaque argument).
Un nombre peut être utilisé en tant que texte.

    print("texte"..tostring(58)) --> texte58
    print("texte"..58) --> texte58
    print(tostring(nil)) --> nil
    print(nil) --> nil

##### La bibliothèque string

Comme pour les nombres, il y a une bibliothèque pour modifier le texte appelée "string".

`string.rep` permet de répeter un texte un certain nombre de fois, par exemple

    print(string.rep("abc", 3)) --> abcabcabc

`string.reverse` permet d'inverser du texte, par exemple

    print(string.reverse("du texte"))) --> etxet ud

`string.lower` et `string.upper` permettent de mettre toutes les lettres en minuscules et en majuscules respectivement.

    print(string.lower("AbCd")) --> abcd
    print(string.upper("AbCd")) --> ABCD

`string.sub` permet de récuperer une partie de texte, le premier caractère est 1, le deuxième 2, etc...
On peut aussi l'utiliser avec des nombres négatifs, c'est à dire que le dernier caractère est -1, l'avant-dernier -2, etc...

    print(string.sub("texte59", 1, 5)) --> texte
    print(string.sub("texte59", -2 -1)) --> 59
    print(string.sub("texte59", -1 -2)) -- ne fonctionne pas dans ce sens

`string.find` cherche un "_pattern_" dans du texte et retourne deux valeurs, le premier caractère qu'il trouve faisant partie du _pattern_ et le dernier (il faut savoir qu'il s'arrête au premier pattern trouvé) ou retourne simplement `nil` si rien n'a été trouvé.

    print(string.find("ENCORE du texte", "texte")) --> 11	15
    print(string.find("eeee", "e")) --> 1	1
    print(string.find("aaa", "b")) --> nil

`string.gsub` remplace un _pattern_ par un autre texte et retourne le nouveau texte et le nombre de substitutions effectuées.

    print(string.gsub("texte", "x", "y")) --> "teyte"	1

`string.byte` convertit chaque caractère (plus exactement octet) en nombre et `string.char` fait l'inverse.

    print(string.byte("a")) --> 97
    print(string.char(97)) --> a
    print(string.byte("xyz")) --> 120
    print(string.byte("xyz", 2)) --> 121
    print(string.byte("xyz", 3)) --> 122
    print(string.char(120, 121, 122)) --> xyz

`string.format` permet de "formater" du texte, je pense qu'un exemple sera plus simple.

    print(string.format("texte%d", 58)) --> texte58
    print(string.format("%f : %.2f", 56.2, 89.1)) --> 56.200000 : 89.10
    print(string.format("[[%s]]", "texte")) --> [[texte]]
    print(string.format("%q", '"')) --> "\""

D'après [le manuel](https://www.lua.org/manual/5.3/manual.html#pdf-string.format), pour `string.format`, Lua utilise la fonction sprintf du C avec quelques différences, les options sont donc documentées dans un manuel de C (comme [celui-là](http://man7.org/linux/man-pages/man3/printf.3.html)).

Il faut noter que les fonctions de cette bibliothèque ne modifient pas vos variables.

    s="abc"
    string.rep(s, 3) --retourne abcabcabc
    print(s) --> abc

Si on voulait changer une variable on pourrait l'écrire de cette façon par exemple :

    s = string.rep(s, 3)

On peut aussi utiliser dans le cas de la bibliothèque string une autre syntaxe.

    s="AbCd"
    print(s:upper()) --> ABCD
    print(s) --> AbCd

Dans ce cas on utilise upper en tant que "_méthode_" sur s.
Utiliser les fonctions de la bibliothèque string en tant que méthodes ne fonctionnera que sur des variables contenant du texte.

Si vous utilisez des lettres hors de la table ACSII (des caractères qui n'éxistent pas en anglais, comme 'é' ou 'ç'), la plupart fonctions de la bibliothèque string fonctionneront toujours (comme `string.rep`), mais pour les autres vous pouvez utiliser la biliothèque utf8.

    print(#"dernière") --> 9
    print(utf8.len("dernière")) --> 8

    print(string.byte("français", 5)) --> 195
    print(string.char(195)) --caractère qui n'éxiste pas
    print(utf8.codepoint("français", 5)) --> 231
    print(utf8.char(231)) --> ç

`utf8.len` peut aussi permettre de vérifier si du texte UTF-8 est correct, si il ne l'est pas il retourne `false` (un booléen, on les verra juste après) et la position de l'octet invalide.

Les fonctions de la bibliothèque string (et aussi certaines d'utf8, comme `utf8.codepoint`) pensent que les positions sont données en octets, ce qui peut être utile parfois, mais peut aussi causer certains problèmes avec l'UTF-8.

    print(string.byte("résumé", 3)) --> 169
    print(string.char(169)) --caractère qui n'éxiste pas

On peut donc utiliser `utf8.offset` pour le texte qui contient des caractères UTF-8.

    s = "résumé"
    print(string.byte(s, utf8.offset(s, 3))) --> 115
    print(string.char(115)) --> s
