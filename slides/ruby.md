!SLIDE

# Programm-ieren mit Ruby

Linuxhotel, Juni 2013
David Roetzel <training@roetzel.de>

!SLIDE

## Über mich

*   Diplom-Informatiker (FH)
*   Freier Berater, Entwickler und Trainer
*   Bonn
*   Webentwicklung seit 1997
*   Ruby seit 2002
*   Rails seit 2005
*   Projekte von Web2.0 bis Intranet

!SLIDE

## Die Schulung

*   5 Tage
*   2 Blöcke von 4h mit jeweils einer Pause
*   Theorie/Praxis gemischt
*   Bitte viel fragen!
*   Schulungsnotebooks mit Ubuntu Linux
*   Handout und Bücher
*   Texteditor Eurer Wahl

!SLIDE

## Themen

*   Montag: Einführung, Grundlagen 
*   Dienstag: Fortsetzung Grundlagen, Klassenbibliothek 
*   Mittwoch: Objektorientierung 
*   Donnerstag: Stdlib, Rubygems, Sinatra
*   Freitag: nach Absprache

!SLIDE

# Ruby

!SLIDE

## Erfinder: Yukihiro "Matz" Matsumoto

![image](matz.jpg)

!SLIDE

## Ruby

*   1995 öffentlich vorgestellt
*   Lange nur in Japan bekannt 
*   Interpretierte Programmiersprache 
*   Objektorientiert 
*   Anleihen bei LISP und Smalltalk
*   Offizielle Implementierung (MRI) und viele Alternativen
*   http://www.ruby-lang.org 

!SLIDE

## Ruby ist...

*   ...objektorientiert.
*   ...elegant.
*   ...schön.
*   ...lesbar.
*   ...Geschmackssache?

!SLIDE

## Wo kann man Ruby nutzen?

*   Originalinterpreter läuft auf allen gängigen Betriebssystemen für Desktop und Server
*   Interpreter für JVM und .Net
*   Rubymotion für iOS-Entwicklung
*   Ruboto für Android
*   Alpha: mruby zur Einbettung in andere Programme

!SLIDE

## Installation

*   Vorinstallierte Version oder Pakete der Distro häufig veraltet
*   Für Windows: [rubyinstaller.org](http://rubyinstaller.org)
*   Für OSX/Linux: rvm oder rbenv/ruby-build

!SLIDE

## RVM: Ruby Version Manager

*   Installation beliebiger Ruby-Versionen
*   Binärpakete und lokales Kompilieren
*   Parallele Installation verschiedener Versionen
*   Bequemes wechseln der Versionen
*   Website: [rvm.io](http://rvm.io)

!SLIDE

## Hello World 

~~~~ruby
#!/usr/bin/env ruby

puts "Hello World"
~~~~~

!SLIDE

## Skripte schreiben

*   Textdateien 
*   Shebang line 
*   Dateirechte 
*   File encodings: \# encoding: utf-8 (Ruby 1.9)
*   Einrücken mit 2 Leerzeichen
*   Hinzuladen externer Dateien mit require 

!SLIDE

## irb

*   interaktive Ruby-Shell 
*   (fast) beliebiger Ruby-Code kann interaktiv ausprobiert werden 
*   Rückgabewert wird sofort angezeigt 
*   Erweiterbar (\~/.irbrc) 

!SLIDE 

## Anweisungen

*   Eine pro Zeile:

~~~~ruby
puts "eins"
puts "zwei"
puts "drei"
~~~~

*   Oder getrennt durch Semikolon:

~~~~ruby
puts "eins" ; puts "zwei" ; puts "drei"
~~~~

*   Kommentare mit \# einleiten 

!SLIDE 

## Lokale Variablen

~~~~ruby
a = 3 # 3
a = b = 4 # 4
a, b = 5, 6 # [5, 6]
~~~~

*   Beginnen mit Kleinbuchstaben, erlaubt sind Buchstaben, Ziffern und Unterstrich
*   Üblich: snake\_case
*   Gültig im jeweiligen Kontext (Datei, Methode, Block, Modul/Klasse)

!SLIDE

## Konstanten

~~~~ruby
PI = 3.14159
~~~~

*   Unveränderliche Werte
*   Beginnen mit Großbuchstaben
*   Üblich: SNAKE\_CASE
*   Gültig global oder innerhalb Modul/Klasse

!SLIDE

## Weitere Variablentypen

*   Instanzen- und Klassenvariablen (später)
*   Globale Variablen (niemals)

!SLIDE

## Einfache Datentypen / Literale

~~~~ruby
5, 3000, 1.39   # Zahlen

'hallo', "test" # Zeichenketten

true, false     # Wahrheitswerte

:name, :running # Symbole

10..20, a..b    # Bereiche

/pattern/, /\s/ # Reguläre Ausdrücke

nil             # Nichts
~~~~

!SLIDE

## Zeichenketten

*   Zeichenketten in einfachen Anführungszeichen werden 1:1 übernommen
*   In doppelten Anführungszeichen sind gewisse Ersetzungen möglich:
    *   Sonderzeichen, z.B. Zeilenumbruch "\n"
    *   Beliebige Ruby-Ausdrücke mit "#{}"

~~~~ruby
name = 'Otto'
"Hallo, #{name}!"
# => 'Hallo, Otto!"
~~~~

!SLIDE

## Alles ist ein Objekt

*   Datentypen in Ruby sind Klassen
*   Werte sind Objekte dieser Klassen (mehr dazu später)
*   Jedes Objekt kann man fragen, von welcher Klasse es ist:

~~~~ruby
5.class         # Fixnum
1.39.class      # Float
'hallo'.class   # String
true.class      # TrueClass
:name.class     # Symbol
(10..20).class  # Range
/pattern/.class # Regexp
~~~~

!SLIDE

## Objekte haben Methoden

~~~~ruby
5.succ             # 6
'hallo'.length     # 5
'hallo'.chop       # "hall"
:name.is_a? Symbol # true
~~~~

*   Klammern, oder nicht klammern? 
*   API-Dokumentation unter [ruby-doc.org](http://ruby-doc.org)

!SLIDE

## Methoden zur Umwandlung

~~~~ruby
23.to_s    # "23"
"42".to_i  # 42
"42".to_f  # 42.0
"3.3".to_f # 3.3

"abc".to_i # 0 (Achtung!)
~~~~

!SLIDE

## "Globale" Methoden

*   Ruby stellt einen Standard-Kontext bereit, in dem bestimmte Methoden immer existent sind
*   Z.B. Basis-Methoden für die Ein- und Ausgabe auf der Konsole:

~~~~ruby
puts "test" # Zeile ausgeben 
test = gets # Zeile einlesen
print "a"   # Kein Umbruch
p "a"       # puts "a".inspect
~~~~

!SLIDE

# Praxis

!SLIDE

## Nachfolger ausgeben

Schreibt ein Programm, das den Benutzer auffordert, eine Ganzzahl einzugeben.

Anschließend soll das Programm den Nachfolger dieser Ganzzahl ausgeben.

!SLIDE

## Operatoren

~~~~ruby
5 + 1     # 6 
5 / 2     # 2 (Achtung!) 
5.0 / 2.0 # 2.5

"Hello" + " World" # "Hello World"

true && true   # true
true and false # false 
true || false  # true
false or true  # true

!true     # false
not false # true
~~~~

!SLIDE

## Kurzformen

*   Aus Operator und Zuweisung lassen sich Kurzformen bilden

~~~~ruby
a = a + 1
a += 1

a ||= 5
a = a || 5
~~~~

!SLIDE

## DRY: Do not Repeat Yourself

*   Niemals mit Copy&Paste programmieren!
*   Kopiert man Code, kopiert man im Zweifel auch Bugs
*   Bevor man 2 oder mehr Zeilen kopiert, besser eine Methode definieren
*   Kleine Unterschiede können durch Parameter realisiert werden

!SLIDE

## Eigene Methoden definieren

~~~~ruby
def add(a, b)
  return a + b
end
~~~~

*   Benennung wie lokale Variablen
*   Zusätzlich gewisse Sonderzeichen erlaubt
*   Beliebige Anzahl Parameter möglich

!SLIDE

## Sonderzeichen in Methodennamen

*   ?, ! und = am Ende des Namens
*   ? für Methoden, die Wahrheitswerte liefern
*   ! für kritische Methoden / Seiteneffekte
*   = für Methoden, die etwas zuweisen
*   Operatoren, wie z.B. +, -, \*, /

!SLIDE

## Default-Parameter

~~~~ruby
def add(a, b = 1)
  return a + b
end

add(3)    # 4
add(3, 5) # 8
~~~~

!SLIDE

## Benannte Parameter (Ruby 2.0)

~~~~ruby
def format_currency(amount: 0.0, currency: 'EUR')
  formatted_amount = sprintf('%.2f', amount)
  "#{formatted_amount} #{currency}"
end

format_currency # 0.00 EUR
format_currency(amount: 23) # 23.00 EUR
format_currency(currency: '$', amount: 6) # 6.00 $
~~~~

!SLIDE

## Rückgabewerte von Methoden

* Stichwort return legt Rückgabewert fest
* return beendet die Abarbeitung der Methode unmittelbar
* Ohne return entscheidet der letzte Ausdruck über den Rückgabewert

!SLIDE

## Rückgabewerte vs. Ausgabe

~~~~ruby
def add(a, b)
  puts a + b
end
add(3,5)

# vs

def add(a, b)
  a + b
end
puts add(3,5)
~~~~

!SLIDE

# Praxis

!SLIDE

## Hello World und Quadratzahlen

*   Schreibt eine hello-world-Methode, die einen personalisierten
    Gruß ausgibt. Dazu soll ein Parameter "name" übergeben werden.
    Anschließend soll der Gruß "Hallo <name>" ausgegeben werden,
    wobei <name> durch den übergebenen Namen ersetzt wird.
*   Schreibt eine Methode, um Quadratzahlen zu berechnen. Als
    Parameter soll eine Zahl übergeben werden. Rückgabewert soll
    das Quadrat der Zahl sein.

Schreibt jeweils einen Aufruf der Methode, der die Funktionsweise
    testet und das Ergebnis auf der Konsole ausgibt.

!SLIDE

# Kontroll-strukturen

!SLIDE

## Fallunterscheidungen 1

~~~~ruby
if a > 1000
  puts "zu groß"
elsif a == 23
  puts "nicht erlaubter Wert"
else
  puts "korrekte Eingabe"
end 

puts "OK" unless a == 23 

(a == 2) ? "zwei" : a.to_s 
~~~~

!SLIDE

## Bedingungen

*   Beliebige Ruby-Ausdrücke können als Bedingungen benutzt werden
*   true ist true, false ist false, nil ist false, alles andere true
*   Kombination mit and/or bzw. &&/||
*   Klammern optional

!SLIDE

## Vergleiche

~~~~ruby
2 == 2         # true
3 == 3.0       # true
3.equal? 3.0   # false

2 != 3         # true
3 > 2          # true, analog <, >=, <=

4 === 4        # true
Fixnum === 4   # true
(1...10) === 4 # true
~~~~

!SLIDE

## Fallunterscheidungen 2

~~~~ruby
case a
when 1
  'Eins'
when 2
  'Zwei'
else
  a.to_s     
end 
~~~~

!SLIDE

## case-Statement 2

~~~~ruby
case var
when Fixnum, Float
  'Zahlwert'
when String
  'Zeichenkette'
else
  'Unbekannter Datentyp'
end
~~~~

!SLIDE

# Praxis

!SLIDE

## Taschenrechner

Schreibt ein Taschenrechnerprogramm, das den Nutzer nacheinander
auffordert eine Zahl, einen Operator und dann noch eine Zahl
einzugeben.

Das Programm soll anhand des Operators die passende Rechnung mit
den beiden Zahlen durchführen und das Ergebnis ausgeben.

!SLIDE

## Schleifen

~~~~ruby
i = 10
while i >= 0 do
  puts "Countdown: #{i}"
  i -= 1
end 

until (i == 0) # ...
~~~~

*   Steuerung mit next, break, redo 

!SLIDE

# Praxis

!SLIDE

## Ratespiel

Schreibt eine Zahlratespiel, das eine zufällige Zahl von 1 bis
10 (oder 100, oder ...) auswählt und den Benutzer so lange die
Zahl raten lässt, bis er korrekt geraten hat.

Bei jedem Durchlauf soll angezeigt werden, um den wievielten
Versuch es sich handelt. Anschließend soll der Nutzer einen
Tipp abgeben können. Das Programm gibt aus, ob der Tipp korrekt
war, oder ob die gesuchte Zahl kleiner oder größer ist als der
abgegebene Tipp.

Ist der Tipp korrekt, beendet sich das Programm. Andernfalls
wird wieder der Versuch angezeigt und um einen neuen Tipp gebeten.
Usw.

!SLIDE

## Arrays

*   Sortierte Liste von Werten

~~~~ruby 
a = [1, 2, 5, 6] 
a[0] # 1 
a = ["hallo", 1, 3.8, :name]
a << 3
a.push(3)
a.pop # 3 # analog unshift/shift
a.first # "hallo", analog last
~~~~

!SLIDE

## Hashes

*   Schlüssel/Wert-Paare 

~~~~ruby
# Allgemeine Syntax
h = {:name => "Otto Mustermann", :straße => "Musterstraße 22",
 :ort => "Musterstadt"}
# Seit 1.9, wenn Schlüssel Symbols sind
h = {name: "Otto Mustermann", straße: "Musterstraße 22",
 ort: "Musterstadt" }

h[:name] \# "Otto Mustermann" 
~~~~

!SLIDE

## Code Blocks

*   Eine Reihe von Anweisungen, die als Parameter an Methoden übergeben werden können
*   Parametrisierbar
*   Die empfangende Methode ist für die Ausführung zuständig (niemals, einmal, mehrmals)
*   Der Code Block behält dabei den äußeren Kontext, auch wenn die Ausführung viel später erfolgt.
*   Komplexe Schleifenkonstrukte möglich, aber auch viele andere Anwendungen

!SLIDE

## Code Blocks - Beispiele

~~~~ruby
loop { puts "Endlos!" }

a = b = 10
5.times do
  a += 1
  b -= 1
end 

5.times { |i| puts i } 
~~~~

!SLIDE

## Iteratoren

~~~~ruby
a = [1, 2, 3] 

a.each { |element| puts element } 
a.each_with_index do |element, i|
  puts "#{i}. #{element}"
end

h = {eins: 1, zwei: 2, drei: 3} 

h.each_key { |key| puts key } 

h.each { |key, value| puts "#{key}: #{value}" }
~~~~

!SLIDE

## select und map

~~~~ruby
a = [1, 2, 3, 4, 5, 6]

a.select {|e| e > 3}

# [4, 5, 6]

a.map {|e| e * 2}

# [2, 4, 6, 8, 10, 12]
~~~~

!SLIDE

## Code Blocks als Objekte

*   Objekte vom Typ Proc
*   Erzeugen mit Proc.new, proc, lambda oder ->
*   Mit lambda erzeugte Procs verhalten sich ein wenig anders
    -   Anzahl Parameter muss eingehalten werden
    -   Verhalten von return
*   call()-Methode zum Ausführen
*   &-Operator zur Umwandlung

!SLIDE

## Methoden, die Code Blocks aufnehmen

~~~~ruby
def benchmark
  puts Time.now
  yield
  puts Time.now
end 

benchmark do
  1000000.times { "23000".to_i }
end
~~~~

!SLIDE

## Code Block erkennen

~~~~ruby
def frame(content = "")
  content = yield if block_given?
  border = "-" * (content.size + 4)
  puts border
  puts "| #{content} |"
  puts border
end

frame("hallo")
frame { "zufall#{rand(1009)}" }
~~~~


!SLIDE

## Code Blocks als Objekte 2

~~~~ruby
def twice(&block)
  2.times &block
end

twice { puts "hallo" }
~~~~

!SLIDE
 
# Praxis

!SLIDE

## Adressdatenbank 1

Schreibt eine Adressdatenbank. Das Programm soll Adressen, die
mindestens Name, Straße und Ort enthalten im Hauptspeicher
ablegen und wieder verfügbar machen.

Dazu präsentiert das Programm dem Benutzer ein Hauptmenü mit
folgenden Möglichkeiten:

Bei der Eingabe von "N" (oder "n") wird ein neuer Datensatz
angelegt. Der Benutzer wird der Reihe nach gebeten, alle
erforderlichen Daten einzugeben.

Bei der Eingabe von "L" (oder "l") werden alle bisher 
eingegebenen Datensätze in verkürzter Form ausgegeben. Die
Darstellung soll nur den Index und den Namen enthalten.

Bei Eingabe eines gültigen Index wird der passende Datensatz
vollständig angezeigt.

Zusätzlich soll es möglich sein, das Programm zu beenden.

!SLIDE

# Weitere Klassen aus Core

!SLIDE

## Reguläre Ausdrücke

*   Mustersuche in Zeichenketten 
*   Starker theoretischer Background 
*   Viel Verwendung in Perl und auf der Shell 
*   In Ruby Objekte 

!SLIDE

## Einfache Ausdrücke

~~~~ruby
/a/ 

/hallo/ 

regexp = /test/

a = "hal"
/#{a}lo/ # /hallo/ 
~~~~

!SLIDE

## Pattern Matching 1

~~~~ruby
"hallo" =~ /a/    # 1 

"hallo" =~ /l/    # 2 

"hallo" =~ /test/ # nil 

"hallo" !~ /p/    # true 

if "hallo" =~ /allo/ ... 
~~~~

!SLIDE

## Pattern Matching 2

~~~~ruby
regexp = /l/
match_data = regexp.match("hallo")

match_data.size       # 1
match_data.pre_match  # "ha"
match_data.post_match # "lo"

/x/.match("hallo")    # nil
~~~~

!SLIDE

## Zeichengruppen

*   Vokale: [aeiou] 
*   Großbuchstaben: [A-Z] 
*   Keine Kleinbuchstaben: [\^a-z] 
*   Ziffern: [0-9] 
*   l,m,n,o: [l-o] 
*   Beliebiges Zeichen: . 
*   /h.llo/ matcht auf "hallo", "hello" usw. 

!SLIDE

## Quantifizierer

*   Ein oder keinmal: ? 
*   Beliebig oft: \* 
*   Beliebig oft, aber mindestens einmal: + 
*   Genau 5 mal: {5}
*   5 mal oder öfter: {5,}
*   5-10 mal: {5,10}

!SLIDE

## Beispiel

*   Variablennamen in Ruby, Versuch 1:

~~~~ruby
/[a-z][a-zA-Z0-9_]*/ 
~~~~

!SLIDE

## Alternativen

*   eine Auswahl zwischen Alternativen wird mit | markiert 

!SLIDE 

## Beispiel

*   (manche) Methodennamen in Ruby:

~~~~ruby
/[a-z][a-zA-Z0-9_]*(\?|!)?/
~~~~

!SLIDE

## Bereichsmarkierungen

*   Zeilenanfang: \^ 
*   Zeilenende: $ 
*   Stringanfang: \\A 
*   Stringende: \\Z 

!SLIDE

## Beispiel

*   Variablennamen in Ruby, Versuch 2:

~~~~ruby
/^[a-z][a-zA-Z0-9\_]*$/ 
~~~~

*   Variablennamen in Ruby, Versuch 3:

~~~~ruby
/\A[a-z][a-zA-Z0-9_]*\Z/ 
~~~~

!SLIDE

## Zeichenklassen

*   \\d entspricht [0-9], \\D [\^0-9] 
*   \\s Whitespace 
*   \\w gültige Zeichen in Bezeichnern ([a-zA-Z0-9\_]) 
*   \\b Wortgrenze 

!SLIDE

## Beispiel

*   Variablennamen in Ruby, Versuch 4:

~~~~ruby
/\A[a-z]\w*\Z/ 
~~~~

!SLIDE 

## Modifizierer

*   Am Ende eines Ausdrucks 
*   Mehrere Kombinierbar 
*   i steht für case-insensitive 
*   m steht für multiline 
*   x für das entfernen von Whitespace 
*   o dafür, Ersetzungen nur einmal vorzunehmen
*   Darüberhinaus weitere für Encoding

!SLIDE

## Die Sache mit der Gier

*   .\* wird häufig benötigt, macht aber oft nicht, was man erwartet 
*   Beispiel HTML-Parsen: /\<.\*\>/ findet nicht einzelne Tags, sondern
    das gesamte Dokument 
*   \* ist greedy (gierig) und sucht den größtmöglichen Match 
*   .\*? sucht den kleinsten Match 

!SLIDE

## Arbeiten mit Matches

*   Für geklammerte Ausdrücke werden gematchte Strings gespeichert (Capturing)

~~~~ruby
"hallo" =~ /h(a)ll(o)/ # 0
$1                     # a
$2                     # o 
~~~~

!SLIDE

## Capturing OO-Style

~~~~ruby
date_exp = /(\d{1,2})\. (\w+) (\d{2,4})/
date_string = "23. Januar 2014"
match_data = date_exp.match(date_string)

match_data.size     # 4
match_data[0]       # "23. Januar 2014"
match_data[1]       # "23"
match_data.captures # ["23", "Januar", "2014"]
~~~~

!SLIDE

## Benannte Gruppen

~~~~ruby
exp = /(?<day>\d{1,2}). (?<month>\w+) (?<year>\d{2,4})/
string = "23. Januar 2014"

match_data = exp.match(string)

match_data[:day]  # "23"
match_data[:month]  # "Januar"
~~~~

!SLIDE

## String\#scan

~~~~ruby
date = "23.01.2014"

date.scan(/\d+/)              # ["23", "01", "2014"]

date.scan(/(\d{2})\.(\d{2})/) # [["23", "01"]]

date.scan(/\d+/) {|match| puts match}
~~~~

!SLIDE

## Suchen & Ersetzen

~~~~ruby
"hallo".sub(/l/, "test")  # "hatestlo" 

"hallo".gsub(/l/, "test") # "hatesttesto" 

"Otto Mustermann".sub(/(\w+)\s+(\w+)/, '\2, \1') # "Mustermann, Otto" 
~~~~

!SLIDE

## Strings teilen

~~~~ruby
"1,2,3".split(",")       # ["1", "2", "3"] 

"1 2  3\n4".split(/\s+/) # ["1", "2", "3", "4"] 
~~~~

!SLIDE 

## Rubular

*   [www.rubular.com](http://www.rubular.com)
*   Schnelles Ausprobieren von (Ruby-)Regular Expressions

!SLIDE

# Praxis

!SLIDE

## Taschenrechner, die zweite

Verbessert das Taschenrechnerprogramm, indem Ihr die Eingabe des
Benutzers in einem einzigen Schritt verlangt und mit Hilfe 
regulärer Ausdrücke auf ihre Gültigkeit prüft.

Hat der Benutzer nicht, wie gefordert, eine Zahl, bzw. einen der
Operatoren +,-,\* und / eingegeben, soll keine Berechnung
erfolgen, sondern eine Fehlermeldung ausgegeben werden.

!SLIDE

## Kommandozeilenargumente

*   Alle Kommandozeilenargumente landen in ARGV 
*   ARGV ist ein Array 
*   ARGV.length nennt Anzahl der Parameter 

!SLIDE

# Praxis

!SLIDE

## Taschenrechner, die dritte

Schreibt den Taschenrechner so um, dass die Eingabe nicht mehr
interaktiv erfolgt, sondern über Kommandozeilenparameter.

So soll der Aufruf des Programms mit den Parametern "1 + 5"
z.B. die Zahlen 1 und 5 addieren.

Die Ausgabe des Ergebnisses soll unmittelbar auf die Standard-
Ausgabe erfolgen. Das Programm ist danach fertig und wird
automatisch beendet.

!SLIDE

## Ein- und Ausgabeströme

*   STDIN, STDOUT, STDERR 
*   puts ist eigentlich STDOUT.puts 
*   gets ist STDIN.gets
*   Eingabestrom kann von der Tastatur eines Benutzers kommen
*   Oder: Programme werden kombiniert - die Ausgabe des einen werden zur Eingabe des anderen
*   Shell-Benutzer kann Ausgabeströme gezielt umleiten

!SLIDE

## Gängige Operationen auf I/O-Objekten

*   Zeilenweise: gets, puts
*   Zeichen/Byte-weise: read, write
*   Gilt für
    *   Ein-/Ausgabeströme
    *   Dateien
    *   Netzwerkkommunikation
    *   usw.

!SLIDE
 
## printf

*   Formatierte Ausgabe von Strings 
*   Platzhalter werden durch Variablen ersetzt 
*   %d für Ganzzahlen, %f für Floats 
*   %.2f – Zeige immer 2 Nachkommastellen 
*   %04d – Zeige Ganzzahlen 4stellig an, fülle Nullen auf 
*   (Analog: sprintf)

!SLIDE

## Datei-E/A

~~~~ruby
f = File.new("test.txt", "r")
f.gets
f.close 

File.open("test.txt", "w") do |file|
  file.puts "Hallo"
end
~~~~

*   "r"ead, "w"rite, "a"ppend (, "b"inary) 

!SLIDE

## Datei zeilenweise verarbeiten

~~~~ruby
File.open("data.txt", "r") do |file|
  file.each_line do |line|
     puts line
  end
end
~~~~

!SLIDE

## Nützliche Helfer

~~~~ruby
File.exists?("/tmp/test.txt")  # false
File.basename("/tmp/test.txt") # "test.txt"
File.dirname("/tmp/test.txt")  # "/tmp"
File.join("tmp", "test.txt")   # "tmp/test.txt"

Dir.mkdir("/tmp/testdir")
Dir.entries("/tmp")       # [...]
Dir.glob("/tmp/*.txt")    # [...]
~~~~

!SLIDE
 
# Praxis

!SLIDE

## Adressdatenbank, die zweite

Erweitert Eure Adressdatenbank, so dass Ihr die Daten
dauerhaft abspeichern und auch wieder einlesen könnt.

!SLIDE

## Datum und Uhrzeit

~~~~ruby
t = Time.now # 2013-05-27 18:21:04 +0200 

t.year       # 2013

t + 60       # 2013-05-27 18:22:04 +0200

t.to_i      # Sekunden seit 01.01.1970 
~~~~

!SLIDE

## Time#strftime

*   Ähnlich printf 
*   %d Tag, %m Monat, %Y Jahr (vierstellig) 
*   Time.now.strftime("%d.%m.%Y") \# "27.05.2013" 

!SLIDE 

# Objekt-orientierung

!SLIDE

## OO

*   Aktuell wichtigstes Programmierparadigma 
*   Stammt u.a. von Smalltalk, entwickelt im Xerox PARC 
*   Wird verwendet in C++, Java, Ruby, Python(, Perl, PHP ...) 
*   Technische Vorteile, aber auch besser an den Menschen angepasst 

!SLIDE 

## Was bedeutet Objektorientierung

*   Ein Softwaresystem besteht aus Objekten, die möglichst nah an der
    realen Welt modelliert sind 
*   Objekte haben Eigenschaften (Attribute) und Verhaltensweisen
    (Methoden) 
*   Objekte schicken sich gegenseitig Nachrichten (Methodenaufruf) 
*   Vererbung ermöglicht es, Gemeinsamkeiten zu teilen 

!SLIDE 

## Ziele aus Entwicklersicht

*   Modellierung in Objekten entspricht eher dem menschlichen Denken 

!SLIDE

## Ziele aus Softwaretechniksicht

*   Bessere Struktur 
*   Stärkere Kapselung 
*   Weniger Redundanz 
*   Wiederverwendbarkeit 
*   Oder zusammengefasst: Modularität

!SLIDE 

## Wichtige Begriffe

*   Klasse (Bauplan) 
*   Instanz (konkretes Objekt, das nach Bauplan der Klasse erstellt wurde) 
*   Instanzenvariable (Eigenschaft des Objekts) 
*   Die Menge aller Instanzenvariablen beschreibt den Zustand eines Objekts 
*   Instanzenmethode 
*   Klassenvariablen und Klassenmethoden 

!SLIDE 

## Klassen entwerfen

*   Welche Objekte soll mein System enthalten? 
*   Was sind die Daten, wer sind die Akteure?
*   Wie sind Zuständigkeiten verteilt?
*   Was kann ich möglicherweise wiederverwenden?
*   Modellierung auf Papier 
*   Modellierung mit UML 

!SLIDE 

## Beispiel Music Player

*  Klassen: Song, Artist, Album
*  Song-Eigenschaften: Titel, Länge usw.
*  Song-Verhaltensweisen: Abspielen, Pausieren usw.

!SLIDE

## Beispiel Büromöbel

*  Klassen: Möbelstück, Stuhl, Tisch
*  Möbelstück-Eigenschaften: Beschreibung, Hersteller usw.
*  Stuhl-Eigenschaften: Sitzhöhe, Armlehnen usw.
*  Tisch-Eigenschaften: Länge, Breite, Höhe usw.
*  Stuhl und Tisch sind beides Möbelstücke und teilen sich die gemeinsamen Eigenschaften

!SLIDE 

## Klassen in Ruby

~~~~ruby
# Einfachste Klasse:
class Song 
end

# Eine Instanz erzeugen:
s = Song.new 
~~~~

*   In einer .rb-Datei darf man beliebig viele Klassen definieren 
*   Best practice: Bei größeren Programmen eine Klasse pro Datei 
*   Code zwischen class und end wird einmalig ausgeführt

!SLIDE

## Noch einmal Methoden

~~~~ruby
class Song
  def play
    puts "playing!"
  end
end
~~~~

*   play ist Instanzenmethode der Klasse Song
*   Mit def self.methodenname definiert man Klassenmethoden 

!SLIDE 

## Das Schlüsselwort "self"

*   "self" im Kontext einer Instanz bezeichnet die Instanz selber 
*   "self" im Kontext einer Klasse, bezeichnet die Klasse 

!SLIDE

## Der Konstruktor

*   Spezielle Methode initialize wird beim Erstellen einer Instanz
    aufgerufen 

~~~~ruby
class Song
  def initialize(title)
  end
end

s = Song.new("Let Her Go")
~~~~

!SLIDE 

## Instanzenvariablen

*   @title ist eine Instanzenvariable 
*   Initialisierung einer Instanzenvariable kann in allen
    Instanzenmethoden erfolgen 
*   Achtung: Testen auf nil 
*   Wenn möglich daher Initialisierung im Konstruktor

!SLIDE

## Zugriff auf Variablen

*   Instanzenvariablen repräsentieren internen Zustand, Zugriff von
    außen nur in Sonderfällen 

~~~~ruby
def title
  return @title
end

def title=(new_title)
  @title = new_title
end
~~~~

*   attr\_reader, attr\_writer, attr\_accessor 

!SLIDE

## Klassenvariablen

*   @@songs\_played ist eine Klassenvariable
*   Existiert genau einmal pro Klasse (inkl. Unterklassen)
*   Übergeordnetes Wissen: Ein einzelner Song **kann** und **muss** nicht wissen, wie viele Songs insgesamt schon gespielt wurden

!SLIDE

# Praxis

!SLIDE

## Bücher

Schreibt eine Klasse, die Bücher repräsentiert.

Ein konkretes Buch soll folgende Eigenschaften haben: Titel, Autor, Seitenzahl, Preis

Alle Eigenschaften sollen von außen les- und schreibbar sein.

Außerdem sollen sie bereits beim instanziieren von Buch-
Objekten übergeben werden.

Die Klasse soll nachhalten, wieviele Bücher instanziiert
wurden und eine Methode bieten, mit der die Anzahl bisher
instanziierter Bücher abgefragt werden kann.

!SLIDE

## DRY Teil2: Vererbung

*   Unterschiedliche Objekte können Gemeinsamkeiten aufweisen
*   Sowohl bei Eigenschaften als auch bei Verhaltensweisen
*   Auch hier bitte kein Copy & Paste
*   Sind es gleichartige Objekte, sollte man Vererbung nutzen
*   Eine Oberklasse enthält alle Gemeinsamkeiten
*   Unterklassen erben von dieser und implementieren nur noch die Unterschiede

!SLIDE

## Vererbung in Ruby

~~~~ruby
class Square < Rectangle
end 
~~~~

*   Square (Quadrat) erbt alle Eigenschaften von Rectangle (Rechteck)
*   (Ein Quadrat ist ein Spezialfall eines Rechtecks) 
*   Das Überschreiben und Ergänzen von Methoden ist möglich 
*   Zugriff auf überschriebene Methoden mit super 

!SLIDE

## Vererbung - Beispiel

~~~~ruby
class Rectangle
  def initialize(width, height)
    @width = width
    @height = height
  end
  def area ; @width * @height ; end
end

class Square < Rectangle
  def initialize(width)
    super(width, width)
  end
end
~~~~

!SLIDE 

## Zugriffschutz

*   **public** (implizit): immer aufrufbar
*   **protected** (Schlüsselwort) : Nur aufrufbar, wenn Empfänger die selbe Klasse hat wie "self"
*   **private** (Schlüsselwort) : Nur auf implizitem self aufrufbar (also nur innerhalb der selben Klasse)

!SLIDE

# Praxis

!SLIDE

## Kaffeemaschine 

!SLIDE

## Fehlerzustände

*   Früher häufig über Rückgabewerte
*   In der OO: Exceptions
*   Exceptions werden im Fehlerfall "geworfen"
*   Exceptions können abgefangen und gezielt behandelt werden
*   Geschieht dies nicht, endet die Abarbeitung des Programms
*   Exceptions sind Objekte, deren Typ und Eigenschaften Aufschluss über das Problem geben

!SLIDE

## Exceptions in Ruby

~~~~ruby
# RuntimeError werfen
raise "Hier ist ein Fehler passiert" 

# Eigene Exception-Typen
class SongNotFoundException < Exception
  def to_s ; "Song file not found" ; end
end 

raise SongNotFoundException
raise SongNotFoundException.new
~~~~

!SLIDE

## Exceptions abfangen

~~~~ruby
begin
  file = File.open("/tmp/test")
  file.write("hallo") 
rescue
  puts "Ein Fehler ist aufgetreten"
ensure
  file.close
end 
~~~~

!SLIDE

## Exceptions unterscheiden

~~~~ruby
begin 
  file = File.open("/tmp/test")
  file.write("hallo") 
rescue IOError
  puts "Ein IOError ist aufgetreten"
rescue SystemCallError
  puts "Ein SystemCallError ist aufgetreten"
end
~~~~

!SLIDE

## Exceptions genauer untersuchen

~~~~ruby
begin 
  file = File.open("/tmp/test")
  file.write("hallo") 
rescue IOError => e
  puts e.message
end
~~~~

!SLIDE

## Exceptions in Methode abfangen

~~~~ruby
def write_into_file(filename, text) 
  file = File.open(filename)
  file.write(text) 
rescue => e
  puts e.message
ensure
  file.close 
end
~~~~

!SLIDE

# Praxis

!SLIDE

## Kaffeemaschine mit Exceptions

Entfernt alle interaktiven Elemente (puts, gets) aus der
Klasse Kaffeemaschine. Ersetzt Ausgaben durch Rückgabewerte
der Methoden.

Erweitert die Klasse Kaffeemaschine um eine Fehlerausgabe mit
Hilfe von Exceptions.

Definiert hierfür eigene Exceptions, die den drei möglichen
Fehlerfällen beim Kaffeekochen entsprechen.

Sorgt dafür, dass beim Auftreten eines Fehlerfalls die
passende Exception geworfen wird.

!SLIDE 

## Module

*   Module können beliebige Klassen, Methoden, Konstanten usw. beinhalten 

~~~~ruby
module MyModule
end 
~~~~

!SLIDE 

## Namespaces

~~~~ruby
module MusicPlayer
  VERSION = "0.0.1"
  class Song 
  end
end 

puts MusicPlayer::VERSION
s = MusicPlayer::Song.new 
~~~~

!SLIDE

## DRY Teil 3: Mixins

*   Vererbung passt logisch nicht immer
*   Bsp: Tisch, Stuhl und User wollen alle loggen, User ist aber kein Möbelstück
*   Resultat sind oft riesiege Vererbungsbäume
*   Statt dessen Mixins: Funktionalität in Klassen hinzuladen
*   Beliebig viele Mixins können pro Klasse inkludiert werden

!SLIDE

## Mixins in Ruby

~~~~ruby
module Logger
  def log(msg) ; puts msg ; end
end 

class User
  include Logger
end 

u = User.new
u.log("hello")
~~~~

!SLIDE

## Klassenmethoden hinzufügen

~~~~ruby
class System
  extend Logger
end

System.log("test")
~~~~

!SLIDE

## Mixin-Benutzung erkennen

~~~~ruby
module MyModule
  def self.included(klass)
    puts "MyModule wurde in #{klass} inkludiert"
  end
  
  def self.extended(klass)
    puts "#{klass} wurde durch MyModule erweitert"
  end
end
~~~~

!SLIDE

## Unit Tests

*   Codeverifikation praktisch unmöglich 
*   Ziel daher: Möglichst gutes automatisiertes, reproduzierbares Testen 
*   Test first: Tests als Spezifikation 
*   Verträgt sich besonders gut mit OO 
*   Test cases und assertions 
*   in Ruby seit 1.9: minitest 

!SLIDE 

## Einfacher Test

~~~~ruby
require "minitest/autorun"

class SongTest < MiniTest::Unit::TestCase
  def test_duration_in_minutes
    song = Song.new('test', 300)
    assert_equal 5, song.duration_in_minutes
  end
end
~~~~

!SLIDE

## Assertions

*   assert / refute 
*   assert\_equal 
*   assert\_instance\_of 
*   assert\_kind\_of 
*   assert\_nil 
*   refute\_nil 
*   assert\_raises
*   assert\_match 

!SLIDE
 
## Setup

~~~~ruby
class SongTest < MiniTest::Unit::TestCase
  def setup
    @song = Song.new('test', 300)
  end

  def test_duration_in_minutes
    assert_equal 5, @song.duration_in_minutes
  end
end
~~~~

!SLIDE 

## Mocking und Stubbing

*   **Unit**-Tests sollen immer nur eine Einheit testen
*   Manche Komponenten sollten beim Testen nicht real ausgeführt werden
*   Andere verlangsamen Tests vielleicht unnötig
*   Wieder andere liefern nicht die zum Testen notwendigen reproduzierbaren Ergebnisse (Time.now !)
*   Bei "Test first"-Ansätzen existieren Komponenten möglicherweise noch gar nicht

!SLIDE

## Mocks und Stubs in minitest

~~~~ruby
mock = MiniTest::Mock.new
mock.expect(:to_s, 'test')
mock.to_s
mock.verify

Time.stub(:now, Time.at(1234567890)) do
  Time.now # 2009-02-14 00:31:30 +0100
end
~~~~

!SLIDE

## Test Driven Development - TDD

*   Aus Test-first entwickelte Vorgehensweise
*   Red-Green-Refactor
    *   Red: Kleinen, *fehlschlagenden* Test schreiben
    *   Green: Code schreiben, bis Test erfolgreich läuft
    *   Refactor: Ergebnis kritisch betrachen, ggf. Umstrukturieren und dabei mit Test absichern

!SLIDE

## Ruby-Testframeworks

*   minitest (seit Ruby 1.9 mitgeliefert) 
*   RSpec 
*   Cucumber 
*   und viele mehr 

!SLIDE

## Tipps zum Testen

*   Test first / TDD ausprobieren
*   Testen lohnt bei großen / langlebigen Projekten fast immer
*   Wenn Testen kompliziert ist, ist das ein Hinweis, dass die Klasse zu komplex ist
*   Wenn ein Bug entdeckt wird, immer erst Test schreiben, dann fixen
*   Auch Tests refactorn
*   Übung macht den Meister

!SLIDE

# Praxis

!SLIDE

##  Kaffeemaschine testen 

Schreibt Tests für Eure Kaffeemaschine.

!SLIDE

## Code Coverage

*   Was ist ein guter Test? 
*   Metriken, z.B. wieviel Code wurde tatsächlich durchlaufen? 
*   Für Ruby z.B. SimpleCov
*   gem install simplecov

!SLIDE

## Ruby-Debugger

*   gem install debugger 
*   Skript debuggen: rdebug skript.rb 
*   Debugger aus Anwendung aufrufen:

~~~~ruby
require "debugger"
#...
debugger 
~~~~

*   Ausdrücke evaluieren 
*   Kommandobsp.: list, where, step, next, break 

!SLIDE

## Core vs. Stdlib

*   Klassen aus Core stehen immer zur Verfügung 
*   Klassen der Stdlib werden mit Ruby zusammen ausgeliefert und können
    als gegeben betrachtet werden 
*   Trotzdem explizites require 

!SLIDE

## CSV-Dateien verarbeiten

*   Bibliothek 'csv' zum Lesen und Schreiben
*   Gängige Eigenschaften können konfiguriert werden, wie z.B.
    -   Trennzeichen
    -   Anführungszeichen
    -   Zeilenumbruch
    -   Kopfzeile
    -   Encoding

!SLIDE

## CSV-Dateien lesen und schreiben

~~~~ruby
require "csv"

CSV.foreach("/tmp/test.csv") do |row|
  p row
end

CSV.open("/tmp/test.csv", "w") do |csv|
  csv << [23,"test",11]
  csv << [42,"hallo", 12]
end
~~~~

!SLIDE

## Logger

*   Simple Bibliothek zum Schreiben von Logfiles
*   Ausgabe in Datei oder Ausgabestrom
*   Log-Level: debug, info, warn, error, fatal, unknown
*   Sinnvolles Standardformat der Nachrichten
*   Rotation von Logdateien

!SLIDE

## Loggen mit Logger

~~~~ruby
require 'logger'

logger = Logger.new("/tmp/logfile.log")
logger.level = Logger::WARN

logger.debug("setup complete")
logger.error("nothing much is happening...")
~~~~

!SLIDE

## Fileutils

*   Methoden, die benannt sind und funktionieren wie auf der Shell
*   Bsp: cp, rm, mv usw.
*   Teilweise mit Parametern
*   Besonders nützlich: mkdir\_p

!SLIDE

## open-uri

*  Entfernte Dateien öffnen, als wären es lokale
*  Unterstützt HTTP(S) und FTP

~~~~ruby
require "open-uri"

open("http://www.linuxhotel.de") do |file|
  file.each_line do |line|
    puts line
  end
end
~~~~

!SLIDE

## Rake

*   Ruby-Variante des bekannten make-Tools 
*   sucht im aktuellen Verzeichnis automatisch nach Datei "Rakefile" 
*   einfache Syntax, aber volle Ruby-Power 
*   rake -T zum Auflisten aller Tasks 
*   Eingebaute Tasks z.B. für Tests 

!SLIDE

## Beispiel Rakefile

~~~~ruby
task :hello do
  puts "hello"
end

task :world do
  puts "world"
end

task :hello_world => [:hello, :world]
~~~~

!SLIDE

## Rake Testtask

~~~~ruby
require "rake/testtask"

Rake::TestTask.new do |t|
  t.pattern = 'test/**/*_test.rb'
end
~~~~

!SLIDE

## Weitere Beispiele Stdlib

*   curses
*   Date
*   dRuby 
*   ERb
*   Networking 
*   ReXML 
*   ... 

!SLIDE

## Rubygems

*   Paketverwaltung für Ruby-Programme und -Bibliotheken 
*   CLI ähnlich apt-get 
*   gem install \<paketname\> 
*   unzählige Pakete verfügbar 
*   rubygems.org 
*   ruby-toolbox.com

!SLIDE 

## Abhängigkeiten managen mit Bundler

*   gem install bundler 
*   Gemfile 
*   bundle install 
*   Lockfile 
*   in der Anwendung:

    require "bundler/setup" 

!SLIDE 

## Rubygems selber bauen

*   Spezifikation in .gemspec-Datei
*   Standardisiertes Verzeichnislayout
*   lib/ für Code, bin/ für ausführbare Dateien
*   Tools helfen beim Generieren, z.B. auch Bundler

!SLIDE

## Beispiel: Rubygem selber bauen

!SLIDE

# Praxis

!SLIDE

## Kaffeemaschinen-Gem bauen

Erstellt ein ausführbares Programm, dass Eure Kaffeemachine interaktiv benutzbar macht.

Paketiert diese Datei, die Kaffeemaschine und Eure Tests als Gem.

!SLIDE

## Webanwendungen mit Sinatra

*   Simpler Ansatz, Webanwendungen mit Ruby zu entwickeln
*   Gegenentwurf zum "schwergewichtigen" Ruby on Rails
*   Sehr einfache API, flexibel erweiterbar
*   Ideal für einfache Anwendungen und Web-APIs
*   gem install sinatra

!SLIDE

## Sinatra DSL

~~~~ruby
require "sinatra"

get '/' do
  "Willkommen"
end

post '/login' do
  "Willkommen #{params[:user]}"
end
~~~~

!SLIDE

## Sinatra-Anwendung

~~~~ruby
require "sinatra/base"

class MyApp < Sinatra::Base

  get '/' do
    "Willkommen"
  end

end
MyApp.run!
~~~~

!SLIDE

## Templates

~~~~ruby
get '/posts/:id' do |id|
  @id = id
  erb :post
end
~~~~

~~~~html
<h3>Post: <%= @id %></h3>
~~~~

!SLIDE

## Layouts

*   Layouts sind Templates, die ein yield enthalten
*   Ideal für üblichen HTML-Rahmen, fixe Header und Footer
*   Default: layout.erb für ERb-Templates
*   Für jedes Template konfigurierbar

!SLIDE

# Praxis

!SLIDE

## Webbasierte Kaffeemaschine

Entwickelt eine Webseite, über die sich Eure Kaffeemaschine fernsteuern lässt.

!SLIDE

# Fazit

!SLIDE

## Jeder fängt mal klein an

~~~~ruby
puts "Hello World"
~~~~

!SLIDE 

## Erste Strukturen

~~~~ruby
def greet(name)
  puts "Hello #{name}"
end
~~~~

!SLIDE

## OO

~~~~ruby
class Greeter

  def initialize(greeting)
    @greeting = greeting
  end

  def greet(name)
    puts "#{greeting} #{name}"
  end

end
~~~~

!SLIDE

## Tolle Ruby-Projekte

*   Web: rails, sinatra, middleman
*   Konfigurationsmanagement: puppet, chef
*   Projektmanagement: redmine
*   Dokumente erzeugen: prawn, axlsx
*   E-Mails: mail, mailman
*   HTML/XML: nokogiri, builder
*   Backup: backup
*   Erweiterungen: active\_support

!SLIDE

## Und jetzt?

*   why's poignant guide 
*   Pickaxe Book
*   Eloquent Ruby von Russ Olsen 
*   The Ruby Programming Language von David Flanagan und Yukihiro
    Matsumoto 
*   www.ruby-lang.org, www.ruby-doc.org 
*   und natürlich: üben, üben, üben 
*   Ruby Koans

!SLIDE

# Noch Fragen?

