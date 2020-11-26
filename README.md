# NeopixelWeihnachtsstern
## ~avatar avatar @unplugged
![Vorschau](https://github.com/r00b1nh00d/NeopixelWeihnachtsstern/blob/master/Stern.gif?raw=true) <br>
Diesmal benötigst du einen Calliope mini und adressierbare RGB-LED's. <br>
Diese LED's findest du entweder unter dem Namen [Neopixel](https://www.google.com/search?q=neopixel+band&rlz=1C1CHBD_deDE928DE928&oq=neopi&aqs=chrome.0.69i59l3j69i57j0j69i60l3.1887j0j9&sourceid=chrome&ie=UTF-8) oder [ws2812b](https://www.ebay.de/sch/i.html?_nkw=ws2812b&_dcat=116022&_sacat=-1&vbn_id=7005777392&LH_PrefLoc=1&_fsrp=1&_sop=15). Ich empfehle einfach ein ws2812b RGB-LED Band von 5m (damit kann man viel anfangen) 

## ~ @unplugged
Um einen Stern mit 5 Spitzen zu basteln habe ich einfach 10 Streifen mit der Schere von meinem 5m Band abgeschnitten. Du kannst den Streifen immer in der Mitte der Kupferkontakte Zerschneiden. <br>
**Hinweis** um weniger LED-Band nutzen zu müssen kannst du auch einen Stern Mit 4 Spitzen und 4 LED's pro Streifen bauen. <br>
![BildZerschneiden](https://github.com/r00b1nh00d/NeopixelWeihnachtsstern/blob/master/StreifenSchneiden.jpeg?raw=true)

## ~ @unplugged
Anschließend habe ich meine 10 Streifen auf ein Stück Pappe in der Form eines Sterns gelegt. Damit für den nächsten Schritt nichts mehr verrutscht habe ich Sie noch mit Klebeband fixiert.<br>
![BildVordemLöten](https://github.com/r00b1nh00d/NeopixelWeihnachtsstern/blob/master/festkleben2.jpg?raw=true)

## ~ @unplugged
Um den elektrischen Kontakt wieder herzustellen habe ich die Ecken wieder zusammen gelötet. An den Stellen wo sich die Streifen berühren kannst du die Kontakte direkt mit dem Lötzinn verbinden.<br>
Die Aüßeren Kontakte sind etwas weiter entfernt, dort macht es Sinn ein kleines Stück Draht für die Verbindung zu nutzen. <br>
 ![Bild beim Löten](https://github.com/r00b1nh00d/NeopixelWeihnachtsstern/blob/master/EckeLoeten.jpg?raw=true)    <br>
Falls du dir noch unsicher beim Löten bist frag am besten deine Eltern oder Lehrer ob Sie dir helfen können.



## ~ @unplugged
Um deinen selbst gebauten Weihnachtsstern an den Calliope anzuschließen kannst du entweder drei kleine Stifte anlöten an die du dann sogenannte Jumperkabel anstecken kannst oder du lötest einfach direkt drei Kabel an eine der Ecken. <br>
Ich habe einfach drei dünnere Kabel genommen: <br>
- für den + Pol habe ich ein rotes Kabel <br>
- für den - Pol habe ich ein schwarzes Kabel <br>
und für das Signal "Din" habe ich ein gelbes Kabel verwendet. <br>
Die anderen Enden habe ich einfach ein Stück weit abisoliert und ganz leicht mit Lötzinn überzogen, so drehen sie sich nicht von alleine auf und ich kann sie später ganz einfach um die Kontakte (goldenen Kreise) am Calliope wickeln. <br>
![Bild Kabel](https://github.com/r00b1nh00d/NeopixelWeihnachtsstern/blob/master/Kabel.jpg?raw=true)


## ~ @unplugged
Jetzt noch die Kabel an den Calliope anschließen.<br>
- plus(+5v) also das rote Kabel an plus (+) vom Calliope anschließen <br>
- minus(GND) also das schwarze Kabel an minus (-) vom Calliope anschließen <br>
und Das gelbe Signalkabel (Din) an den Pin 1 (1) vom Calliope anschließen <br>

![bild Anschlüsse](https://github.com/r00b1nh00d/NeopixelWeihnachtsstern/blob/master/Anschluss.jpg?raw=true)

## ~ @unplugged
Jetzt kommen wir zur Programmierung. Ich zeige dir hier ein kleines Beispiel aber du kannst anschließend deine eigene Animation Programmieren, welche mit Sicherheit noch besser aussieht.

## Schritt 1
``||basic: beim Start||`` musst du dem Calliope sagen wo du die LED-Streifen angeschlossen hast. Erstelle dazu eine Variable ``||variables: Stern||`` und speicher mit dem Block "Neopixel at Pin P0 With 24 Leds"  und ``||variables: setze auf|``, dass der Neopixel am Pin P1 angeschlossen ist und wie viele LED's du für deinen Stern benutzt hast. <br>
Das hintere Feld mit dem RGB-Format ist erstmal uninteressant (du brauchst es nur sollte bei deinen LED's die Farben vertauscht sein also grün leuchten wenn aber rot programmiert wurde) <br>
Ich habe für meine Stern 60 LED's benötigt.
```blocks
let Stern = neopixel.create(DigitalPin.P1, 60, NeoPixelMode.RGB)

``` 

## Schritt 2
Für meinen Stern wollte ich die meisten LED's rot leuchten lassen und nur ein Paar grün. <br>
Das ganze sollte sich dann dauerhaft drehen.<br>
Dazu habe ich die LED's mit einer Schleife rot gefärbt und die restlichen grün.
**Hinweis** Wenn du eine Veränderung am Neupixel anzeigen möchtest brauchst du auch immer den Block "show".

```block
let Stern = neopixel.create(DigitalPin.P1, 12, NeoPixelMode.RGB)
for (let Index = 0; Index <= 9; Index++) {
    Stern.setPixelColor(Index, neopixel.colors(NeoPixelColors.Red))
}
Stern.setPixelColor(10, neopixel.colors(NeoPixelColors.Green))
Stern.setPixelColor(11, neopixel.colors(NeoPixelColors.Green))
Stern.show()
```


## Schritt 3
Um jetzt noch alles drehen zu lassen einfach den Block rotiere und eine kurze Pause in den Dauerhaft Block. **und nicht den Block "show" vergessen**
```blocks
basic.forever(function () {
    Stern.rotate(1)
    Stern.show()
    basic.pause(50)
})
```

