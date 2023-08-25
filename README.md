<p align='center'>
<img src ="https://d31uz8lwfmyn8g.cloudfront.net/Assets/logo-henry-white-lg.png">
<p>

<h1 align='center'>
 <b>PROYECTO INDIVIDUAL Nº2</b>
</h1>
 
# <h1 align="center">**`Cryptocurrency Market Data Analytics`**</h1>
¡Bienvenidos al último proyecto individual 2 de la etapa de labs! En esta ocasión, deberán hacer un trabajo situándose en el rol de un ***Data Analyst***.
<p align='center'>
<img src = 'https://www.clarin.com/img/2023/06/14/WJlAYJhAg_360x240__1.jpg' height = 200>
<p>

# Contexto

Como Analistas de Datos en la empresa de servicios financieros ***ACInvest Inc***, que se ha interesado en el mercado de criptomonedas debido a su crecimiento exponencial y al potencial de oportunidades de inversión para los clientes. La empresa, me asignó la tarea de realizar un análisis exhaustivo que permita entender mejor el mercado de criptomonedas para presentar los hallazgos y recomendaciones en un informe detallado.


![logo intro](./Images/Acinvest_trans.png)

## Contenido

- [Requisitos](#requisitos)
- [Configuración del Entorno](#configuración-del-entorno)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Extraccion de datos](#extraccion-de-datos)
- [Análisis Exploratorio](#análisis-exploratorio)
- [Modelo de Predicción](#modelo-de-predicción)
- [KPIs](#kpis)
- [Resultados y Visualizaciones](#resultados-y-visualizaciones)
- [Conclusiones](#conclusiones)
- [Bibliografía](#bibliografía)



## Requisitos

- Python 3.11+
- Bibliotecas requeridas: pandas, sqlalchemy,matplotlib, seaborn, mysql-connector-python, yfinance, pycoingecko.

## Configuración del Entorno

1. Clona este repositorio.
2. Instala las bibliotecas requeridas utilizando el comando:

pip install -r requirements.txt

## Extraccion de datos
La extraccion de datos se realizó desde las siguinetes APIs:
1. API CoinGecko para extraer información sobre la moneda en sí misma (USD). El procedimiento se detalla en este archivo [API Coingecko](Notebook/data_extrac_API_Coingecko.ipynb)
2. API Binance para obtener los precios de apertura cierre, maximos minimos y spread. El procedimiento se detalla en este archivo [API Binance](Notebook/data_spread_API_Binance.ipynb)
3. API yfinance para obtener los precios históricos diarios de los bonos del tesoro de USA. El procedimiento se detalla en este archivo [API yfinance](Notebook/data_bonos_API_yfinance.ipynb)

Estos datos fueron almacenados en una base de datos con el nombre de `cripto_db` en MySQL, para luego ser consumidos en los analisis posteriores.

## ***Estructura de los datos en cripto_db***

![Tablas y columnas almacenadas en la base de datos](./Images/tablas_db.png)

## Estructura del Proyecto

|-- Dataset/
| |-- df_cripto.csv
| |-- df_total.csv
| |-- df_spread.csv
| |-- df_bonos_usa.csv
|-- Notebooks/
| |-- bonos_database.ipynb
| |-- cripto_database.ipynb
| |-- data_bonos_API_yfinance.ipynb
| |-- data_extrac_API_Coingecko.ipynb
| |-- data_spread_API_Binance.ipynb
| |-- data_totalvol_trade_API_Binance.ipynb
| |-- eda.ipynb
| |-- spread_database.ipynb
| |-- total_volumen_API_Binance.ipynb
|-- README.md
|-- requirements.txt


## Análisis Exploratorio

El análisis exploratorio se realiza en el notebook [eda.ipynb](Notebook/eda.ipynb) Se exploran los datos de criptomonedas, se generan visualizaciones para comprender tendencias y patrones en los precios, capitalización de mercado, volumen y más.

En este análisis exploratorio, hemos examinado datos relacionados con criptomonedas, incluyendo precios, capitalización de mercado, volumen de negociación y otras métricas relevantes. Se han escogido las 10 principales monedas basadas en el mator volumen de capitalización. El objetivo es comprender mejor las tendencias y patrones en el mercado de criptomonedas a lo largo del tiempo. En nuestro análisis hemos incorporado además datos de los bonos del Tesoro de los estados unidos a fin de determinar la influencia de estos datos en el mercado ya que son un indice muy utilizado para valorar tanto el riesgo como el rendimiento en el mercado de inversiones.

**Exploración de Precios y Capitalización de Mercado**

Hemos examinado los precios y la capitalización de mercado de las 10 principales criptomonedas. Se observa que Bitcoin (BTC) ha sido consistentemente una de las criptomonedas con el precio más alto y la mayor capitalización de mercado a lo largo de los años. Ethereum (ETH) también muestra una tendencia alcista en términos de precio y capitalización. Otras criptomonedas, como Ripple (XRP) y Litecoin (LTC), muestran variaciones en sus precios y capitalización.

**Análisis de Volumen de Negociación**

El volumen de negociación es un indicador importante de la liquidez y el interés en una criptomoneda. Observamos picos en el volumen de negociación en momentos de alta volatilidad en el mercado, lo que sugiere que los inversores están activamente comprando y vendiendo. Estos picos pueden estar relacionados con eventos clave en el mundo de las criptomonedas o factores económicos más amplios, hemos buscado posibles correlaciones o patrones entre los movimientos del mercado de criptomonedas y los cambios en los precios de los bonos del Tesoro de los Estados Unidos.

**Anomalías y Outliers**

Durante el análisis, identificamos valores atípicos (outliers) en los datos de precios y capitalización de mercado. Estos valores pueden indicar eventos extraordinarios en el mercado, como cambios drásticos en el precio en un corto período de tiempo. Es importante investigar y comprender la causa de estas anomalías antes de tomar decisiones basadas en los datos.

**Contribuciones de Criptomonedas al Precio Total**

Hemos explorado la contribución de cada criptomoneda al precio total del mercado, teniendo en cuenta la influencia de los bonos del Tesoro.Observamos que Bitcoin (BTC) y Ethereum (ETH) tienen las contribuciones más significativas al precio total. Otras criptomonedas pueden tener una contribución menor en comparación.

## Modelo de Predicción

Este modelo indica que existe una relación negativa moderada entre el rendimiento de los bonos del Tesoro y el rendimiento de las criptomonedas. Esto significa que, en general, un aumento del rendimiento de los bonos del Tesoro se asociará con una disminución del rendimiento de las criptomonedas.

Esta relación negativa se puede explicar por varios factores. En primer lugar, los inversores suelen considerar las criptomonedas como una clase de activos de riesgo, similar a las acciones. Cuando los rendimientos de los bonos del Tesoro son bajos, los inversores están más dispuestos a asumir riesgos, lo que puede conducir a un aumento de los precios de las criptomonedas. Sin embargo, cuando los rendimientos de los bonos del Tesoro aumentan, los inversores pueden optar por vender sus acciones y comprar bonos del Tesoro, lo que puede conducir a una caída de los precios de las criptomonedas.

En segundo lugar, los bonos del Tesoro son una inversión segura, lo que los convierte en un refugio seguro en tiempos de incertidumbre. Cuando los mercados financieros son turbulentos, los inversores pueden optar por vender sus acciones y comprar bonos del Tesoro, lo que puede conducir a una caída de los precios de las criptomonedas.

Sin embargo, es importante tener en cuenta que la relación entre el rendimiento de los bonos del Tesoro y el rendimiento de las criptomonedas no es perfecta. Hay otros factores que pueden afectar a los precios de las criptomonedas, como la inflación, la política monetaria de la Reserva Federal y la situación económica mundial.

Aquí hay algunos ejemplos de cómo los inversores pueden utilizar esta información:

* Un inversor que busque reducir su exposición al riesgo podría optar por vender sus criptomonedas si los rendimientos de los bonos del Tesoro aumentan.
* Un inversor que busque aprovechar la volatilidad de las criptomonedas podría optar por comprar criptomonedas si los rendimientos de los bonos del Tesoro disminuyen.



## KPIs

***Dominancia del Mercado:***
La dominancia del mercado se refiere a la proporción del valor total del mercado de criptomonedas que corresponde a una criptomoneda específica. Puede proporcionar información sobre la posición relativa de una criptomoneda en comparación con el mercado en su conjunto. Una mayor dominancia podría indicar una criptomoneda más influyente en el mercado.
La dominancia del mercado esta relacionada a la liquidez. La liquidez es la facilidad con la que un activo puede ser comprado o vendido sin afectar significativamente su precio. Una criptomoneda con una alta dominancia del mercado es más líquida, lo que significa que es más fácil comprar y vender sin afectar su precio. Esto es importante para los inversores porque les ayuda a reducir el riesgo de pérdidas.

***Rendimiento histórico:*** Este KPI es importante para comprender cómo una criptomoneda ha funcionado en el pasado. Sin embargo, es fundamental recordar que el rendimiento histórico no garantiza el rendimiento futuro, especialmente en el caso de las criptomonedas debido a su alta volatilidad y a otros factores.
El rendimiento es la cantidad de ganancias o pérdidas que ha obtenido una inversión en un período de tiempo determinado. Una criptomoneda con un buen rendimiento histórico es más probable que continúe creciendo en el futuro. Sin embargo, es importante tener en cuenta que el rendimiento pasado no es garantía de rendimiento futuro.

***Volatilidad:*** La volatilidad es un factor distintivo de las criptomonedas y puede ser tanto una oportunidad como un riesgo. Para los inversores que buscan obtener ganancias a corto plazo, la volatilidad puede ser útil. Sin embargo, para aquellos que buscan inversiones más estables y a largo plazo, la volatilidad puede ser un desafío. 
La volatilidad es un indicador importante del riesgo asociado a una criptomoneda. Las criptomonedas con una alta volatilidad son más propensas a fluctuaciones de precios significativas, lo que puede generar pérdidas para los inversores.

***Capitalización de mercado:*** La capitalización de mercado esclave para ev aluar el tamaño relativo de una criptomoneda en comparación con otras. Puede proporcionar información sobre la adopción y la importancia de una criptomoneda en el mercado.
La capitalización de mercado esta asociada al tamaño. El tamaño es la cantidad de dinero que está invertido. Una criptomoneda con una capitalización de mercado alta es más grande, lo que significa que es más probable que sea adoptada por los inversores y los consumidores.

En resumen, los KPIs de criptomonedas son importantes para evaluar el potencial de una criptomoneda porque son indicadores de su popularidad, aceptación, rendimiento histórico, volatilidad y tamaño. Estos KPIs pueden ser utilizados por los inversores para tomar decisiones informadas sobre dónde invertir sus fondos.


## Conclusiones

El análisis en el contexto de las criptomonedas nos ha proporcionado una visión general de las tendencias, patrones y volatilidad en el mercado. Si bien el análisis nos ha permitido entender mejor el comportamiento pasado, es esencial reconocer la naturaleza especulativa y volátil de las criptomonedas al tomar decisiones financieras. Los modelos de predicción y análisis estadísticos deben utilizarse con precaución y junto con una comprensión completa del mercado y sus riesgos.

## Resultados y Visualizaciones

Los resultados del análisis exploratorio se presentan en forma de visualizaciones en los notebooks correspondientes. Además, se generan gráficos de diferentes tipos para mostrar tendencias, contribuciones y otros aspectos relevantes de los datos.

## Bibliografía

https://ambcrypto.com/bitcoian-all-factors-leading-up-to-the-worst-decline-of-2023/

https://www.globenewswire.com/news-release/2023/05/01/2658095/28124/en/Europe-Blockchain-and-Cryptocurrency-Market-Analysis-Report-2023-Europe-Witnesses-Gradual-Adoption-of-Digital-Assets-Amidst-the-Fall-of-the-Crypto-Market.html

https://home.treasury.gov/data/treasury-coupon-issues-and-corporate-bond-yield-curves/treasury-coupon-issues

https://home.treasury.gov/resource-center/data-chart-center/interest-rates/TextView?type=daily_treasury_yield_curve&field_tdr_date_value=2023

https://home.treasury.gov/data/treasury-coupon-issues-and-corporate-bond-yield-curves/treasury-coupon-issues

https://es.statista.com/estadisticas/1236380/bitcoin-valor-de-capitalizacion-bursatil-a-nivel-mundial/

https://www.criptonoticias.com/analisis-investigacion/altibajos-precio-bitcoin-historia/
