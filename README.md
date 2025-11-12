<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exploración Vocacional - Autoconocimiento</title>
    <style>
        :root {
            --primary: #4a6fa5;
            --secondary: #6b8cbc;
            --light: #f5f7fa;
            --dark: #333;
            --accent: #ff7e5f;
            --success: #4caf50;
            --error: #f44336;
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: var(--light);
            color: var(--dark);
            line-height: 1.6;
            padding: 20px;
        }
        
        .container {
            max-width: 1000px;
            margin: 0 auto;
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0,0,0,0.1);
            padding: 30px;
            position: relative;
        }
        
        h1, h2, h3 {
            color: var(--primary);
            margin-bottom: 15px;
        }
        
        h1 {
            text-align: center;
            margin-bottom: 30px;
            border-bottom: 2px solid var(--secondary);
            padding-bottom: 15px;
        }
        
        .section {
            margin-bottom: 40px;
            padding: 20px;
            border-radius: 8px;
            background-color: #f9f9f9;
            border-left: 4px solid var(--secondary);
            display: none;
        }
        
        .section.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .section-title {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 15px;
        }
        
        .section-number {
            background-color: var(--primary);
            color: white;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
        }
        
        th, td {
            border: 1px solid #ddd;
            padding: 12px;
            text-align: left;
        }
        
        th {
            background-color: var(--primary);
            color: white;
        }
        
        tr:nth-child(even) {
            background-color: #f2f2f2;
        }
        
        input[type="text"], textarea, select {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 16px;
            transition: border-color 0.3s;
        }
        
        input[type="text"]:focus, textarea:focus, select:focus {
            border-color: var(--primary);
            outline: none;
            box-shadow: 0 0 5px rgba(74, 111, 165, 0.3);
        }
        
        input[type="checkbox"] {
            transform: scale(1.2);
            margin-right: 8px;
        }
        
        .checkbox-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 10px;
            margin: 15px 0;
        }
        
        .checkbox-item {
            display: flex;
            align-items: center;
            margin-bottom: 8px;
            padding: 8px;
            border-radius: 4px;
            transition: background-color 0.2s;
        }
        
        .checkbox-item:hover {
            background-color: rgba(74, 111, 165, 0.1);
        }
        
        button {
            background-color: var(--primary);
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s;
            margin: 10px 5px;
        }
        
        button:hover:not(:disabled) {
            background-color: var(--secondary);
        }
        
        button:disabled {
            background-color: #cccccc;
            cursor: not-allowed;
        }
        
        .save-btn {
            background-color: var(--success);
        }
        
        .save-btn:hover:not(:disabled) {
            background-color: #3d8b40;
        }
        
        .visualization {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            margin: 30px 0;
            gap: 20px;
        }
        
        .circle-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin: 0 10px;
        }
        
        .circle-label {
            margin-top: 10px;
            font-weight: bold;
            color: var(--primary);
            text-align: center;
        }
        
        .circle {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            border: 2px solid var(--primary);
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 15px;
            background-color: white;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }
        
        .circle textarea {
            border: none;
            background: transparent;
            resize: none;
            text-align: center;
            height: 100%;
        }
        
        .circle textarea:focus {
            box-shadow: none;
        }
        
        .nav-buttons {
            display: flex;
            justify-content: space-between;
            margin-top: 30px;
        }
        
        .progress-container {
            display: flex;
            align-items: center;
            margin-bottom: 30px;
            gap: 15px;
        }
        
        .progress-bar {
            height: 10px;
            background-color: #e0e0e0;
            border-radius: 5px;
            flex-grow: 1;
            overflow: hidden;
        }
        
        .progress {
            height: 100%;
            background-color: var(--accent);
            width: 0%;
            transition: width 0.5s;
        }
        
        .progress-text {
            font-weight: bold;
            color: var(--primary);
            white-space: nowrap;
        }
        
        .section-counter {
            text-align: center;
            margin-bottom: 10px;
            font-weight: bold;
            color: var(--primary);
        }
        
        .error-message {
            color: var(--error);
            font-size: 14px;
            margin-top: 5px;
            display: none;
        }
        
        .success-message {
            background-color: var(--success);
            color: white;
            padding: 15px;
            border-radius: 4px;
            margin: 20px 0;
            text-align: center;
            display: none;
        }
        
        @media (max-width: 768px) {
            .checkbox-grid {
                grid-template-columns: 1fr;
            }
            
            .circle {
                width: 130px;
                height: 130px;
            }
            
            .visualization {
                gap: 10px;
            }
            
            .nav-buttons {
                flex-direction: column;
                gap: 10px;
            }
            
            .nav-buttons button {
                width: 100%;
            }
        }
        
        @media (max-width: 480px) {
            .circle {
                width: 120px;
                height: 120px;
                font-size: 14px;
            }
            
            .container {
                padding: 15px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Exploración Vocacional y Autoconocimiento</h1>
        
        <div class="progress-container">
            <div class="progress-bar">
                <div class="progress" id="progress"></div>
            </div>
            <div class="progress-text" id="progressText">0%</div>
        </div>
        
        <div class="section-counter">
            <span id="currentSection">1</span> de <span id="totalSections">4</span>
        </div>
        
        <!-- Sección 1.A: Explorar Gustos e Intereses -->
        <section class="section active" id="section1">
            <div class="section-title">
                <div class="section-number">1</div>
                <h2>EXPLORAR GUSTOS E INTERESES</h2>
            </div>
            <p>Completá el siguiente cuadro prestando especial atención a la consigna de cada columna.</p>
            
            <table>
                <thead>
                    <tr>
                        <th>Lo que hago en mi tiempo libre</th>
                        <th>Las materias que más me gustan</th>
                        <th>Los temas que me interesan</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><input type="text" id="tiempo_libre1" aria-label="Actividad de tiempo libre 1"></td>
                        <td><input type="text" id="materias1" aria-label="Materia favorita 1"></td>
                        <td><input type="text" id="temas1" aria-label="Tema de interés 1"></td>
                    </tr>
                    <tr>
                        <td><input type="text" id="tiempo_libre2" aria-label="Actividad de tiempo libre 2"></td>
                        <td><input type="text" id="materias2" aria-label="Materia favorita 2"></td>
                        <td><input type="text" id="temas2" aria-label="Tema de interés 2"></td>
                    </tr>
                    <tr>
                        <td><input type="text" id="tiempo_libre3" aria-label="Actividad de tiempo libre 3"></td>
                        <td><input type="text" id="materias3" aria-label="Materia favorita 3"></td>
                        <td><input type="text" id="temas3" aria-label="Tema de interés 3"></td>
                    </tr>
                    <tr>
                        <td><input type="text" id="tiempo_libre4" aria-label="Actividad de tiempo libre 4"></td>
                        <td><input type="text" id="materias4" aria-label="Materia favorita 4"></td>
                        <td><input type="text" id="temas4" aria-label="Tema de interés 4"></td>
                    </tr>
                </tbody>
            </table>
            
            <table>
                <thead>
                    <tr>
                        <th>Algo que me gustó hacer</th>
                        <th>Soy bueno/a para</th>
                        <th>En mi futuro no puede faltar</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><input type="text" id="gusto1" aria-label="Actividad que gustó hacer 1"></td>
                        <td><input type="text" id="bueno1" aria-label="Habilidad 1"></td>
                        <td><input type="text" id="futuro1" aria-label="Elemento futuro importante 1"></td>
                    </tr>
                    <tr>
                        <td><input type="text" id="gusto2" aria-label="Actividad que gustó hacer 2"></td>
                        <td><input type="text" id="bueno2" aria-label="Habilidad 2"></td>
                        <td><input type="text" id="futuro2" aria-label="Elemento futuro importante 2"></td>
                    </tr>
                    <tr>
                        <td><input type="text" id="gusto3" aria-label="Actividad que gustó hacer 3"></td>
                        <td><input type="text" id="bueno3" aria-label="Habilidad 3"></td>
                        <td><input type="text" id="futuro3" aria-label="Elemento futuro importante 3"></td>
                    </tr>
                    <tr>
                        <td><input type="text" id="gusto4" aria-label="Actividad que gustó hacer 4"></td>
                        <td><input type="text" id="bueno4" aria-label="Habilidad 4"></td>
                        <td><input type="text" id="futuro4" aria-label="Elemento futuro importante 4"></td>
                    </tr>
                </tbody>
            </table>
            
            <div class="error-message" id="section1Error">Por favor, completa al menos un campo en cada columna.</div>
        </section>
        
        <!-- Sección 1.B: ¿Qué palabras me describen? -->
        <section class="section" id="section2">
            <div class="section-title">
                <div class="section-number">2</div>
                <h2>¿QUÉ PALABRAS ME DESCRIBEN?</h2>
            </div>
            <p>Seleccioná, en cada columna, aquellas palabras que te parece que pueden describir tu forma de ser.</p>
            
            <table>
                <thead>
                    <tr>
                        <th>Soy</th>
                        <th>Me gusta</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>
                            <div class="checkbox-item">
                                <input type="checkbox" id="soy_introvertido">
                                <label for="soy_introvertido">Introvertido/a</label>
                            </div>
                        </td>
                        <td>
                            <div class="checkbox-item">
                                <input type="checkbox" id="gusta_analizar">
                                <label for="gusta_analizar">Analizar hechos científicos</label>
                            </div>
                        </td>
                    </tr>
                    <tr>
                        <td>
                            <div class="checkbox-item">
                                <input type="checkbox" id="soy_intuitivo">
                                <label for="soy_intuitivo">Intuitivo/a</label>
                            </div>
                        </td>
                        <td>
                            <div class="checkbox-item">
                                <input type="checkbox" id="gusta_observar">
                                <label for="gusta_observar">Observar</label>
                            </div>
                        </td>
                    </tr>
                    <tr>
                        <td>
                            <div class="checkbox-item">
                                <input type="checkbox" id="soy_imaginativo">
                                <label for="soy_imaginativo">Imaginativo/a y fantasioso/a</label>
                            </div>
                        </td>
                        <td>
                            <div class="checkbox-item">
                                <input type="checkbox" id="gusta_experimentar">
                                <label for="gusta_experimentar">Experimentar</label>
                            </div>
                        </td>
                    </tr>
                    <tr>
                        <td>
                            <div class="checkbox-item">
                                <input type="checkbox" id="soy_calculador">
                                <label for="soy_calculador">Calculador/a</label>
                            </div>
                        </td>
                        <td>
                            <div class="checkbox-item">
                                <input type="checkbox" id="gusta_diagnosticar">
                                <label for="gusta_diagnosticar">Diagnosticar</label>
                            </div>
                        </td>
                    </tr>
                    <tr>
                        <td>
                            <div class="checkbox-item">
                                <input type="checkbox" id="soy_sensible">
                                <label for="soy_sensible">Sensible</label>
                            </div>
                        </td>
                        <td>
                            <div class="checkbox-item">
                                <input type="checkbox" id="gusta_ensenar">
                                <label for="gusta_ensenar">Enseñar</label>
                            </div>
                        </td>
                    </tr>
                </tbody>
            </table>
            
            <div class="error-message" id="section2Error">Por favor, selecciona al menos una opción en cada columna.</div>
        </section>
        
        <!-- Sección 1.C: Diferenciando gustos e intereses -->
        <section class="section" id="section3">
            <div class="section-title">
                <div class="section-number">3</div>
                <h2>DIFERENCIANDO GUSTOS E INTERESES</h2>
            </div>
            <p>Seleccioná <strong>no más de dos áreas</strong> que te parezca que responden mejor a tu forma de ser.</p>
            
            <div class="checkbox-grid">
                <div class="checkbox-item">
                    <input type="checkbox" id="area_ciencias" class="area-checkbox">
                    <label for="area_ciencias">CIENCIAS</label>
                </div>
                <div class="checkbox-item">
                    <input type="checkbox" id="area_artes" class="area-checkbox">
                    <label for="area_artes">ARTES</label>
                </div>
                <div class="checkbox-item">
                    <input type="checkbox" id="area_humanidades" class="area-checkbox">
                    <label for="area_humanidades">HUMANIDADES</label>
                </div>
                <div class="checkbox-item">
                    <input type="checkbox" id="area_economia" class="area-checkbox">
                    <label for="area_economia">ECONOMÍA - ADMINISTRACIÓN</label>
                </div>
                <div class="checkbox-item">
                    <input type="checkbox" id="area_tecnico" class="area-checkbox">
                    <label for="area_tecnico">TÉCNICO/A</label>
                </div>
                <div class="checkbox-item">
                    <input type="checkbox" id="area_social" class="area-checkbox">
                    <label for="area_social">SOCIAL</label>
                </div>
            </div>
            
            <div class="error-message" id="section3Error">Por favor, selecciona máximo dos áreas.</div>
        </section>
        
        <!-- Sección 1.D: Visualizate -->
        <section class="section" id="section4">
            <div class="section-title">
                <div class="section-number">4</div>
                <h2>VISUALIZATE</h2>
            </div>
            <p>Completá los siguientes círculos con una sola idea principal para cada uno:</p>
            
            <div class="visualization">
                <div class="circle-container">
                    <div class="circle">
                        <textarea id="circle1" placeholder="Escribe aquí..." rows="3" maxlength="100" aria-label="Lo que me gusta hacer"></textarea>
                    </div>
                    <div class="circle-label">Lo que me gusta hacer</div>
                </div>
                <div class="circle-container">
                    <div class="circle">
                        <textarea id="circle2" placeholder="Escribe aquí..." rows="3" maxlength="100" aria-label="Para lo que soy bueno"></textarea>
                    </div>
                    <div class="circle-label">Para lo que soy bueno</div>
                </div>
                <div class="circle-container">
                    <div class="circle">
                        <textarea id="circle3" placeholder="Escribe aquí..." rows="3" maxlength="100" aria-label="Lo que me parece importante"></textarea>
                    </div>
                    <div class="circle-label">Lo que me parece importante</div>
                </div>
                <div class="circle-container">
                    <div class="circle">
                        <textarea id="circle4" placeholder="Escribe aquí..." rows="3" maxlength="100" aria-label="Lo que creo que el mundo necesita"></textarea>
                    </div>
                    <div class="circle-label">Lo que el mundo necesita</div>
                </div>
            </div>
            
            <div class="error-message" id="section4Error">Por favor, completa todos los círculos antes de continuar.</div>
            
            <div style="margin-top: 30px; padding: 15px; background-color: #e8f4fd; border-radius: 8px;">
                <p><strong>Descubrí que:</strong></p>
                <ul>
                    <li>Entre lo que te gusta y aquello en lo que sos bueno/a está <strong>TU POTENCIAL</strong>.</li>
                    <li>Entre lo que te gusta y lo que te parece importante están <strong>TUS OBJETIVOS</strong>.</li>
                    <li>Entre lo que te parece importante y lo que crees que el mundo necesita está <strong>TU CAMPO LABORAL</strong>.</li>
                    <li>Entre lo que crees que el mundo necesita y aquello en lo que sos bueno/a está <strong>TU APORTE AL MUNDO</strong>.</li>
                </ul>
            </div>
        </section>
        
        <div class="success-message" id="successMessage">
            ¡Tus respuestas se han guardado correctamente!
        </div>
        
        <div class="nav-buttons">
            <button id="btnPrev" disabled>Anterior</button>
            <button id="btnNext">Siguiente</button>
            <button class="save-btn" id="btnSave">Guardar Respuestas</button>
        </div>
    </div>
<script>
document.addEventListener('DOMContentLoaded', function() {
    // Elementos DOM
    const sections = document.querySelectorAll('.section');
    const prevBtn = document.getElementById('btnPrev');
    const nextBtn = document.getElementById('btnNext');
    const saveBtn = document.getElementById('btnSave');
    const successMessage = document.getElementById('successMessage');
    
    // Variables de estado
    let currentSection = 0;
    const totalSections = sections.length;
    
    // Inicialización - mostrar primera sección
    sections[currentSection].classList.add('active');
    updateButtons();
    
    // NAVEGACIÓN
    prevBtn.addEventListener('click', function() {
        if (currentSection > 0) {
            sections[currentSection].classList.remove('active');
            currentSection--;
            sections[currentSection].classList.add('active');
            updateButtons();
        }
    });
    
    nextBtn.addEventListener('click', function() {
        if (currentSection < totalSections - 1) {
            sections[currentSection].classList.remove('active');
            currentSection++;
            sections[currentSection].classList.add('active');
            updateButtons();
        }
    });
    
    // BOTÓN GUARDAR - FUNCIÓN SIMPLE
    saveBtn.addEventListener('click', function() {
        // Recopilar todos los datos
        const datosGuardados = {
            seccion1: obtenerDatosSeccion1(),
            seccion2: obtenerDatosSeccion2(), 
            seccion3: obtenerDatosSeccion3(),
            seccion4: obtenerDatosSeccion4(),
            fechaGuardado: new Date().toLocaleString()
        };
        
        // Guardar en localStorage
        localStorage.setItem('misRespuestasVocacionales', JSON.stringify(datosGuardados));
        
        // Mostrar mensaje de éxito
        successMessage.style.display = 'block';
        
        // Ocultar mensaje después de 3 segundos
        setTimeout(() => {
            successMessage.style.display = 'none';
        }, 3000);
        
        console.log('Datos guardados:', datosGuardados);
        alert('¡Tus respuestas se guardaron correctamente!');
    });
    
    // Función para actualizar botones
    function updateButtons() {
        prevBtn.disabled = currentSection === 0;
        nextBtn.disabled = currentSection === totalSections - 1;
    }
    
    // FUNCIONES PARA OBTENER DATOS
    function obtenerDatosSeccion1() {
        const datos = {};
        
        // Obtener datos de la tabla 1
        datos.tiempoLibre = [
            document.getElementById('tiempo_libre1').value,
            document.getElementById('tiempo_libre2').value,
            document.getElementById('tiempo_libre3').value,
            document.getElementById('tiempo_libre4').value
        ].filter(valor => valor.trim() !== '');
        
        datos.materias = [
            document.getElementById('materias1').value,
            document.getElementById('materias2').value,
            document.getElementById('materias3').value,
            document.getElementById('materias4').value
        ].filter(valor => valor.trim() !== '');
        
        // ... agregar más campos si necesitas
        
        return datos;
    }
    
    function obtenerDatosSeccion2() {
        const datos = {
            palabrasSoy: [],
            palabrasGusta: []
        };
        
        // Obtener checkboxes marcados "Soy"
        document.querySelectorAll('[id^="soy_"]:checked').forEach(checkbox => {
            datos.palabrasSoy.push(checkbox.nextElementSibling.textContent);
        });
        
        // Obtener checkboxes marcados "Me gusta"
        document.querySelectorAll('[id^="gusta_"]:checked').forEach(checkbox => {
            datos.palabrasGusta.push(checkbox.nextElementSibling.textContent);
        });
        
        return datos;
    }
    
    function obtenerDatosSeccion3() {
        const areasSeleccionadas = [];
        
        document.querySelectorAll('.area-checkbox:checked').forEach(checkbox => {
            areasSeleccionadas.push(checkbox.nextElementSibling.textContent);
        });
        
        return { areas: areasSeleccionadas };
    }
    
    function obtenerDatosSeccion4() {
        return {
            circulo1: document.getElementById('circle1').value,
            circulo2: document.getElementById('circle2').value,
            circulo3: document.getElementById('circle3').value,
            circulo4: document.getElementById('circle4').value
        };
    }
});
</script>
</body>
</html>
