Particle Dallas Temperature sensor library
===

This library is a port of the Arduino Dallas Temperature Sensor library. Some includes have been fixed, but the library is otherwise untouched.

Optimized for local Particle development by [Nathan Robinson](https://github.com/nrobinson2000).

_**Note:** This library depends on the OneWire library, so be sure to include it in your project too._

Original repository by Miles Burton: [Arduino-Temperature-Control-Library](https://github.com/milesburton/Arduino-Temperature-Control-Library).

This library was forked from [SparkCoreDallasTemperature](https://github.com/tomdeboer/SparkCoreDallasTemperature) by Tom de Boer.

> This library supports the following devices:
> 
> 
> * DS18B20
> * DS18S20 - Please note there appears to be an issue with this series.
> * DS1822
> * DS1820
>
>
> You will need a pull-up resistor of about 5 KOhm between the 1-Wire data line
> and your 5V power. If you are using the DS18B20, ground pins 1 and 3. The
> centre pin is the data line '1-wire'.


### Example code
>Prints the temperature in Celsius every 500 milliseconds.

```cpp
#include "Particle.h"
#include "spark-dallas-temperature/spark-dallas-temperature.h"

// Init Dallas on pin digital pin D3
DallasTemperature dallas(new OneWire(D3));

void setup()
{
  Serial.begin(9600);
  dallas.begin();
}
	
void loop()
{
  dallas.requestTemperatures();
  float celsius = dallas.getTempCByIndex(0);
  Serial.printlnf("Temperature = %1.3f *C", celsius);
  delay(500);
}
	
```

### Get this library using [po-util](https://github.com/nrobinson2000/po-util)

This library can be easily downloaded using po-util's library manager:
```sh
$ po lib get https://github.com/nrobinson2000/spark-dallas-temperature
```
You'll probably want to download `OneWire` as well:
```sh
$ po lib get https://github.com/spark/OneWireLibrary OneWire
```

The two libraries can be added to a project easily:
```sh
$ po lib add spark-dallas-temperature
$ po lib add OneWire
```
