# Twilio In-Browser Calling Application

## Descripción

Esta es una aplicación web que permite realizar y recibir llamadas telefónicas directamente desde el navegador utilizando la API de Twilio Programmable Voice. La aplicación está construida con Python (Flask) en el backend y JavaScript en el frontend.

## ⚠️ Importante: Origen del Código

**Este proyecto NO es de mi autoría original.** Es un fork/clon de un tutorial completo de Twilio que explica paso a paso cómo implementar llamadas en el navegador.

### Tutorial Original
Para ver el tutorial completo paso a paso, visita:
**https://www.twilio.com/es-mx/blog/make-receive-phone-calls-browser-twilio-programmable-voice-python-javascript**

## 🚀 Características

- ✅ Realizar llamadas salientes desde el navegador
- ✅ Recibir llamadas entrantes en el navegador
- ✅ Interfaz de usuario moderna con modales
- ✅ Integración completa con Twilio Voice API
- ✅ Manejo de eventos de llamada (conectar, desconectar, rechazar)

## 📋 Prerrequisitos

Antes de comenzar, necesitarás:

1. **Cuenta de Twilio** con:
   - Account SID
   - API Key SID
   - API Key Secret
   - Número de teléfono de Twilio
   - TwiML App SID

2. **ngrok** instalado y configurado
   - Guía de instalación: https://gist.github.com/wosephjeber/aa174fb851dfe87e644e

3. **Python 3.x** con pip

## 🛠️ Instalación y Configuración

### 1. Clonar/Descargar el Proyecto
```bash
git clone <url-del-repositorio>
cd tutorial-twilio-in-browser-calling-start
```

### 2. Instalar Dependencias
```bash
pip install -r requirements.txt
```

Si no existe el archivo requirements.txt, instala manualmente:
```bash
pip install flask twilio python-dotenv
```

### 3. Configurar Variables de Entorno

Crea un archivo `.env` en la raíz del proyecto con las siguientes variables:

```env
TWILIO_ACCOUNT_SID=tu_account_sid_aqui
TWILIO_API_KEY_SID=tu_api_key_sid_aqui
TWILIO_API_KEY_SECRET=tu_api_key_secret_aqui
TWIML_APP_SID=tu_twiml_app_sid_aqui
TWILIO_NUMBER=tu_numero_twilio_aqui
```

**⚠️ Importante:** Si cambias estas variables, también debes actualizar el archivo `main.py` donde están hardcodeadas las credenciales.

### 4. Configurar Twilio

1. Ve a la [Consola de Twilio](https://console.twilio.com/)
2. Navega a **Phone Numbers > Manage Numbers > Active Numbers**
3. Selecciona tu número de Twilio
4. En la sección "Voice & Fax", configura:
   - **Configure With:** TwiML App
   - **TwiML App:** Selecciona la app que creaste

### 5. Configurar ngrok

1. Inicia ngrok apuntando al puerto 3000:
```bash
ngrok http 3000
```

2. Copia la URL HTTPS que te proporciona ngrok (ej: `https://abc123.ngrok.io`)

3. Ve a tu TwiML App en la consola de Twilio y actualiza la URL del webhook con:
   ```
   https://tu-url-ngrok.ngrok.io/handle_calls
   ```

**⚠️ Nota:** Cada vez que reinicies ngrok, obtendrás una URL diferente y deberás actualizar la configuración de TwiML App.

## 🚀 Ejecución

### 1. Iniciar el Servidor Flask
```bash
python main.py
```

El servidor se ejecutará en `http://localhost:3000`

### 2. Iniciar ngrok (en otra terminal)
```bash
ngrok http 3000
```

### 3. Acceder a la Aplicación
Abre tu navegador y ve a `http://localhost:3000`

## 📱 Uso de la Aplicación

### Realizar Llamadas Salientes
1. Haz clic en el botón verde del teléfono
2. Ingresa el número de teléfono en el modal
3. Haz clic en "Call"
4. La llamada se conectará a través del navegador

### Recibir Llamadas Entrantes
1. Espera a que aparezca "Twilio.Device Ready!" en la página
2. Llama al número de Twilio desde cualquier teléfono
3. Aparecerá un modal para aceptar o rechazar la llamada
4. Haz clic en el botón verde para aceptar o rojo para rechazar

## 📁 Estructura del Proyecto

```
tutorial-twilio-in-browser-calling-start/
├── main.py                          # Servidor Flask principal
├── .env                             # Variables de entorno (crear)
├── static/
│   ├── css/
│   │   └── style.css               # Estilos CSS
│   ├── js/
│   │   ├── main.js                 # Lógica principal de Twilio
│   │   └── modals.js               # Manejo de modales
│   └── images/
│       └── user.png                # Imágenes
└── templates/
    ├── home.html                   # Página principal
    ├── dial_modal.html             # Modal para marcar
    ├── call_in_progress_modal.html # Modal de llamada en progreso
    └── incoming_call_modal.html    # Modal de llamada entrante
```

## 🔧 Configuración de Desarrollo

### Modo Debug
El servidor Flask ya está configurado en modo debug por defecto:
```python
app.run(host='0.0.0.0', port=3000, debug=True)
```

### Logs
Los logs de la aplicación aparecerán en la consola donde ejecutes `python main.py`.

## 🐛 Solución de Problemas

### Error: "Could not get a token from server!"
- Verifica que las credenciales en `.env` sean correctas
- Asegúrate de que el servidor Flask esté ejecutándose
- Revisa la consola del navegador para errores específicos

### Error: "Address already in use"
- El puerto 3000 está ocupado, detén otros procesos o cambia el puerto

### Llamadas no conectan
- Verifica que ngrok esté ejecutándose
- Confirma que la URL de ngrok esté actualizada en TwiML App
- Revisa los logs del servidor Flask

## 📚 Recursos Adicionales

- [Documentación de Twilio Voice](https://www.twilio.com/docs/voice)
- [SDK de Twilio Client JS](https://www.twilio.com/docs/voice/client)
- [Documentación de Flask](https://flask.palletsprojects.com/)

## 📄 Licencia

Este proyecto es un fork educativo basado en el tutorial oficial de Twilio. Consulta los términos de uso de Twilio para más información.

---

**Nota:** Este proyecto es únicamente para fines educativos y de desarrollo. Para uso en producción, considera las mejores prácticas de seguridad y escalabilidad. 