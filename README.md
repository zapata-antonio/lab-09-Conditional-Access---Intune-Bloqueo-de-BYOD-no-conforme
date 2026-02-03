
# LAB 09 — Bloqueo de BYOD no conforme

## Contexto (por qué hice este lab)
En entornos reales, un problema típico es el acceso desde dispositivos personales (BYOD) sin control:  
PCs sin cifrado, sin antivirus corporativo, sin políticas, etc.

La idea de este laboratorio es simple:  
si el dispositivo **no está enrolado** y **no cumple** (no es *compliant*), **se bloquea el acceso** aunque el usuario tenga la contraseña correcta.

---

## Objetivo
Bloquear el acceso a aplicaciones corporativas desde dispositivos BYOD **no conformes**, usando:

- **Conditional Access**
- Requisito: **dispositivo marcado como compatible (compliant)**

---

## Qué configuré
Creé una política de Acceso Condicional que:
- se aplica al usuario de pruebas (`usuario_4`)
- afecta a **Office 365** (entrada típica: portal.office.com / myapps.microsoft.com)
- y exige que el dispositivo sea **compliant**

Si el dispositivo no está enrolado o no cumple, el acceso se bloquea.

---

## Pasos realizados
1. Creé la política `LAB09 - Bloqueo BYOD no conforme` con el requisito **Require compliant device**.
2. Probé el acceso desde ventana de incógnito (dispositivo sin enrolar).
3. Verifiqué el bloqueo en los **Sign-in logs**, confirmando que el motivo es el estado de compliance del dispositivo.

---

## Evidencias

### 01) Política de Conditional Access creada (Require compliant device)
[<img src="images/01-ca-policy-byod-noncompliant.png" width="800">](images/01-ca-policy-byod-noncompliant.png)

### 02) Acceso bloqueado desde BYOD no conforme
[<img src="images/02-blocked-by-device-compliance.png" width="800">](images/02-blocked-by-device-compliance.png)

### 03) Sign-in logs: la política se aplica y bloquea por no compliance
[<img src="images/03-signinlogs-ca-blocked.png" width="800">](images/03-signinlogs-ca-blocked.png)

---

## Checklist
- [x] Se creó una política de Acceso Condicional para BYOD no conforme
- [x] El usuario de pruebas fue bloqueado aunque la contraseña era correcta
- [x] El bloqueo se validó en Sign-in logs (Conditional Access)

---

## Qué explicaría en una entrevista
“Para evitar accesos desde dispositivos personales sin control, uso Conditional Access exigiendo que el dispositivo esté marcado como compliant.  
Así, aunque el usuario tenga credenciales correctas, si el dispositivo no cumple las políticas de seguridad (enrolado / compliant), el acceso se bloquea y queda trazabilidad en los logs.”
